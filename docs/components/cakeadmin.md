CakeAdmin Component
===================

The CakeAdmin Component is a bridge between your application,

[doc_toc]

Loading
-------

You can load the component in your AppController:

public function initialize() {
    $this->loadComponent('CakeAdmin.CakeAdmin');
}

> Note: The PostTypes Component is default loaded on CakeAdmin related Controllers.


Usage
-----

The CakeAdmin Component has some functional method you can use to communicate with the CakeAdmin Panel.

### Administrators
By calling `$this->CakeAdmin->administrators()` you will get a list of administrators of CakeAdmin. For example:

    // will return an array with all admin-data:
    $this->CakeAdmin->administrators();

    // will return a list with as key the `id`, and value the chosen field (email):
    $this->CakeAdmin->administrators('email');
    // for example:
    //    [
    //        1 => 'bob@cakemanager.org'
    //    ]

### IsLoggedIn and AuthUser
The `isLoggedIn`-method can be used to check if an administrator is logged in. When you want to get his data you can use
the `authUser` method:

    // will return a bool:
    $this->CakeAdmin->isLoggedIn();

    // will return an array with session-data (if logged in):
    $this->CakeAdmin->authUser();

### RecipientList
When you add the component to your controller, you automatically have the recipientList `administrators` added to the
Notifier-plugin.

> Note: To read more about recipientLists for notifications, read:
https://github.com/cakemanager/cakephp-notifier#recipientlists