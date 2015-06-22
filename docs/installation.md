Installation
============

This section gives a brief description how to install the CakeAdmin Plugin and it's requirements.

[doc_toc]

Requirements
------------

- A fresh copy of CakePHP 3.x
- Composer

Getting the CakeManager
-----------------------

You can get the plugin by running the following command:

    composer require cakemanager/cakephp-cakeadmin:dev-master

After that we need to load our plugin.
Use your shell...

    $ bin/cake plugin load -b -r CakeAdmin
    
... or use your `config/bootstrap.php`:

    Plugin::load('CakeAdmin', ['bootstrap' => true, 'routes' => true]);

Creating the tables
-------------------

    $ bin/cake migrations migrate -p CakeAdmin
    
This command tells the Migrations-plugin to migrate (install) the CakeAdmin tables.

Creating an user
----------------

Now you need an administrator-account to login. Run the following command in your shell:

    $ bin/cake admin newAdmin
    
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