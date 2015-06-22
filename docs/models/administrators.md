AdministratorsModel
====================

The AdministratorsModel handles the administrators of your application.

[doc_toc]

Columns
-------

The used table to store administrators MUST contain the following columns:
- `email`
- `password`
- `activation_key`

The columns `email` and `password` can be changed by the `Configure`-class of CakePHP:

    Configure::write('CA.fields', [
        'username' => 'username',
        'password' => 'psswrd'
    ]);
    
From now on, adminstrators will be logged in with the columns `username` and `psswrd`.

Custom Model
------------

If you want to use your own model as AdministratorsModel, use this Configuration:

    // WARNING: NOT IMPLEMENTED YET
    Configure::write('CA.AdministratorsModel', 'CustomModel');
    
> Note: this feature is not implemented yet.

