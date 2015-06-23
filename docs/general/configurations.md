Configurations
==============

The following configurations area available for the CakeAdmin Plugin. All configurations are prefixed with the `CA`-
prefix.

[doc_toc]

Fields
------

Changing the login-fields can be done with `CA.fields`:

    Configure::write('CA.fields', [
        'username' => 'email',
        'password' => 'password'
    ]);

PostTypes
---------

PostTypes are stored under the `CA.PostTypes`-key. You shouldn't modify that data.

Models
------

Under the `CA.Models` key all models to create PostTypes of are stored. Use the following example to add a model:

    Configure::write('CA.Models.blogs', 'Blogs');
    
Theming
-------

The default theme and layouts for the admin panel are changeable by this keys:

    // Changing the theme
    Configure::write('CA.theme', 'LighStrap');
     
    // Changing the default layout
    Configure::write('CA.layout.default', 'customDefault');
    
    // Changing the login layout (for unauthorized pages)
    Configure::write('CA.layout.login', 'customLogin');