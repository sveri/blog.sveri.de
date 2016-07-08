---
id: 171
title: Zend_Acl / Zend_Auth / Zend_Navigation
date: 2011-03-18T23:12:36+00:00
author: sveri
layout: post
guid: http://blog.sveri.de/index.php?/archives/164-guid.html
permalink: /2011/03/18/zend_acl-zend_auth-zend_navigation/
categories:
  - Uncategorized
---
Today i was looking for a nice tutorial about how to use Zend_Acl to check on every page request if the user has the right to access the controller/action. Now, there are some infos about that out there, but either they&#8217;re outdated, or not useable, cause the code is incomplete, or doesnt work at all.  
So this is the solution i came up with during the day. I will start at the entry point, the Bootstrap.php.





</p> 

  1. protected function _initAuth() {          
    $this->bootstrap(&#8218;frontController&#8216;);          
    // set up the roles and resources          
    $acl = H\_Plugin\_Acl::getInstance();          
    $fc = $this->getResource(&#8218;frontController&#8216;);          
    // check the rights vs. the roles          
    $fc->registerPlugin(new H\_Plugin\_Accescontrol($acl), 10);      
    }


  2. Now, my acl class:  
    class H\_Plugin\_Acl extends Zend_Acl  
    {      
    const ROLE_GUEST = &#8218;guest&#8216;;      
    const ROLE_ADMIN = &#8218;admin&#8216;;      
    protected static $_instance;      
    / **Singleton pattern** /      
    protected function __construct()      
    {          
    $this->addRole(new Zend\_Acl\_Role(self::ROLE_GUEST));          
    $this->addRole(new Zend\_Acl\_Role(self::ROLE\_ADMIN), self::ROLE\_GUEST);          
    $this->addResource(new Zend\_Acl\_Resource(&#8218;index&#8216;))               
    ->addResource(new Zend\_Acl\_Resource(&#8218;admin&#8216;))               
    ->addResource(new Zend\_Acl\_Resource(&#8218;auth&#8216;))              
    ;          
    $this->allow(&#8218;guest&#8216;, &#8218;index&#8216;);          
    $this->allow(&#8218;guest&#8216;, &#8218;auth&#8216;);          
    $this->allow(&#8218;admin&#8216;, &#8218;admin&#8216;);          
    return $this;      
    }      
    public static function getInstance()      
    {          
    if (null === self::$_instance) {              
    self::$_instance = new self();          
    }          
    return self::$_instance;      
    }  
    }


  3. Now, the class to check the user against the acl:  
    class H\_Plugin\_Accescontrol extends Zend\_Controller\_Plugin_Abstract {      
    private $auth;      
    private $acl;      
    public function _\_construct(Zend\_Acl $acl){          
    $this->auth = Zend_Auth::getInstance();          
    $this->acl = $acl;      
    }      
    public function preDispatch(Zend\_Controller\_Request_Abstract $request) {          
    if ($this->auth->hasIdentity()){// && Zend_Registry::isRegistered(&#8217;strRole&#8216;)){              
    // fetchbyloginname calls a ModelMapper, and the method retrieves the user from db which is logged in              
    // also have a look at: [https://github.com/sveri/ZFP](https://github.com/sveri/ZFP "https://github.com/sveri/ZFP") where we have set up a nice caching system for zend              
    $objBenutzer = Model_BenutzerMapper::getCachedInstance()->fetchByLoginname($this->auth->getIdentity());              
    $role = $objBenutzer->getRole();              
    Zend_Registry::set(&#8217;numBenutzerId&#8216;, $objBenutzer->getId());              
    Zend_Registry::set(&#8217;strRole&#8216;, $objBenutzer->getRole());          
    } else {              
    $role = &#8218;guest&#8216;;          
    }          
    $resource = $request->getControllerName();          
    if (!$this->acl->has($resource)) {              
    $resource = null;          
    }          
    if (!$this->acl->isAllowed($role, $resource)) {              
    if ($this->auth->hasIdentity()) {                  
    // angemeldet, aber keine Rechte -> Fehler!                  
    $request->setModuleName(&#8218;default&#8216;);                  
    $request->setControllerName(&#8218;error&#8216;);                  
    $request->setActionName(&#8218;forbidden&#8216;);              
    } else {                  
    //nicht angemeldet -> Login                  
    $request->setModuleName(&#8218;default&#8216;);                  
    $request->setControllerName(&#8218;index&#8216;);                  
    $request->setActionName(&#8218;index&#8216;);              
    }          
    }      
    }  
    }


  4. And finally the navigation with acl, which is very simple, this is what i have in my standard layout.phtml:  
    $HPN = new H\_Plugin\_Navigation();  
    $nav = $HPN->getNav();  
    $acl = H\_Plugin\_Acl::getInstance();  
    $strRole = null;  
    if(Zend_Registry::isRegistered(&#8217;strRole&#8216;)){      
    $strRole = Zend_Registry::get(&#8217;strRole&#8216;);  
    }  
    echo $this->navigation($nav)->menu()->setAcl($acl)->setRole($strRole);
</ol> 



Thats basically it, my user table consists of at least 3 entries: role, loginname, passwort, where role is an enum of all the available roles in the Zend_Acl.  
This is a very basic example, of course you can get that all cached, read the roles und rules from db, etc. but for small projects, thats most of the times to much overhaul <img src="http://blog.sveri.de/templates/default/img/emoticons/smile.png" alt=":-)" style="display: inline; vertical-align: bottom;" class="emoticon" />



Ah, and not to forget, i wont paste the Zend_Auth class here, cause thats pretty standard, something that can be found everywhere <img src="http://blog.sveri.de/templates/default/img/emoticons/smile.png" alt=":-)" style="display: inline; vertical-align: bottom;" class="emoticon" />