Custom Controllers
==================

In this short tutorial we will explain how to add your custom controllers to the CakeAdmin panel.

[doc_toc]

Creating a new Controller
-------------------------

First you need a controller like this:

    namespace App\Controller\Admin;
    
    use CakeAdmin\Controller\AppController;
    
    class CustomController extends AppController
    {
    
        public function index() {
        
        }
        
    }

Explanation:
- The namespace uses a prefix: `App\Controller\Admin`.
- The class `CustomController` extends to the `AppController` of the `CakeAdmin` plugin.


Adding a menu-item
------------------

Our next step is to add a menu-item to the menu-bar. This can be done in your `config/bootstrap.php`:


    Configure::write('CA.Menu.main.custom', [
        'url' => [
            'prefix' => 'admin',
            'controller' => 'Custom',
            'plugin' => false
        ]
    ]);

    
Done!
-----

Congratulations! You've added your own controller to the CakeAdmin panel. Happy coding!
