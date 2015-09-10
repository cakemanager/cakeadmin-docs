Installation
============

This section gives a brief description how to install the CakeAdmin Plugin and its requirements.

[doc_toc]

Requirements
------------

- A fresh copy of CakePHP 3.x
- Composer

Getting the CakeAdmin Plugin
----------------------------

You can get the plugin by running the following command:

    composer require cakemanager/cakephp-cakeadmin:dev-master

After that we need to load our plugin.
Use your shell...

    $ bin/cake plugin load -b -r CakeAdmin
    
... or use your `config/bootstrap.php`:

    Plugin::load('CakeAdmin', ['bootstrap' => true, 'routes' => true]);

Installation
------------

Now you need to migrate the plugin and its dependencies. There is an easy way to install the whole plugin in once:

    $ bin/cake cainstall
    
This command will prepare everything for the CakeAdmin Plugin. At the end of the installation you have to enter your
e-mailaddress and password (won't be hidden!).

If you have trouble with this way of commands, run the following:
-    `$ bin/cake migrations migrate -p CakeAdmin`
-    `$ bin/cake migrations migrate -p Notifier`		
-    `$ bin/cake migrations migrate -p Settings`

Creating an user
----------------

If you need multiple administrators, run the following command in your shell to create an administrator:

    $ bin/cake admin
    
This command will request your e-mailaddress and (shown!) password.

Done
----

Congratulations! You are ready to login at `yourwebsite.com/login`! After you logged in you are able to manage your 
data, expand the back and and use many CakeAdmin-compatible plugins.

Further reading
---------------

Here are some suggestions related to this section:

- CakePHP's [Quick Start](http://book.cakephp.org/3.0/en/quickstart.html) for 3.x.
- [WILL BE EXPANDED SOON]().
