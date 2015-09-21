Quick Start
===========

So... You are going to try the CakeAdmin Plugin? You won't regret! In this tutorial we will install the plugin, talk
about it's features, and start using it. Ready?

Before you start, remember we always want to get in touch with you! Do you have trouble, do you need help, or do you have
some awesome ideas? Get in touch with us via [Gitter](https://gitter.im/cakemanager/cakephp-cakeadmin)!

[doc_toc]

Installation
------------

It takes the following steps to install the CakeAdmin Plugin into your cake project:

### Composer

    composer require cakemanager/cakephp-cakeadmin:1.0.x

### Load

    $ bin/cake plugin load -b -r CakeAdmin

### Install

    $ bin/cake cainstall

This command will migrate the plugin and its dependencies. After the migration, you will be able to create your first
administrator user. Do you want to create another one? You can do it in the admin-panel, or use the shell:

    $ bin/cake admin

> Note: Want a detailed description of installing the plugin? Take a look at:
[Installation](/docs/cakeadmin/1.0/installation).

Features
--------

So, you are all set! The CakeAdmin Plugin has been installed and you are able to login. Go to `yourwebsite.com/admin`.

### Dashboard
After you have logged in you will start at the Dashboard. In here you will see the recent blogs by the CakeManager Team.
Also you will get the tools to start quickely: quick start, docs, plugins, and more! We have added this dashboard to
give you the tools to start, and help you as much as possible.

> Note: In a following release you will be able to customize the dashboard, and add your own 'widgets'. This will make
your dashboard more helpful for yourself and other developers!

### Administrators
On the left you will find the 'Administrators'-button. Here you will be able to manage all administrators. Who are
administrators? Well, that's you, and other developers who are working on your project.

> Note: Note that other administrators are able to remove your account, or change your password.

> Note: In a following release you will be able to add roles to adminstators. This will create a hierarchy in your user
management.

### Settings
The CakeAdmin Plugin uses the [Settings Plugin](https://github.com/cakemanager/cakephp-settings). This enables you to
manage your settings via your database. The CakeAdmin Plugin adds a nice feature: In here the settings are categorized
per prefix, and you are able to manage them inside this panel.

Try to add your own setting by adding the following to your `config/bootstrap.php`:

    use Settings\Core\Setting;
    Setting::register('App.Description', 'This is my first application using CakeAdmin');

> Note: Read more about Settings here: https://github.com/cakemanager/cakephp-settings

Usage
-----

Now, you will start to expand your admin-panel. Use the following SQL to add the `blogs`-table to your database:

```
CREATE TABLE `blogs` (
	`id` INT(11) NOT NULL AUTO_INCREMENT,
	`title` VARCHAR(255) NULL DEFAULT NULL,
	`body` TEXT NULL,
	`image` VARCHAR(250) NULL DEFAULT NULL,
	`featured` VARCHAR(250) NULL DEFAULT NULL,
	`category_id` INT(11) NULL DEFAULT NULL,
	`created_by` INT(11) NULL DEFAULT NULL,
	`modified_by` INT(11) NULL DEFAULT NULL,
	`created` DATETIME NULL DEFAULT NULL,
	`modified` DATETIME NULL DEFAULT NULL,
	`filename` VARCHAR(50) NULL DEFAULT NULL,
	PRIMARY KEY (`id`)
);
```

Now run the command:

    $ bin/cake bake model Blogs

We want to have a feature in our application, that people can read blogs in your application. We will manage those
blogs in the admin-panel. Just add the following to your `BlogsModel`:

```
public function postType() {
    return [
        'formFields' => [
            '_create' => [
                'type' => 'file'
            ],
            'id',
            'title',
            'body',
            'category_id',
            'image' => [
                'type' => 'file'
            ]
        ],
        'tableColumns' => [
            'id',
            'title',
            'category_id' => [
                'get' => 'category.name'
            ],
            'created',
            'created_by' => [
                'get' => 'created_by.email'
            ]
        ],
        'contain' => [
            'Categories'
        ]
    ];
}
```

As last, you need to let CakeAdmin know you want to manage this Model by adding the following code to your
`config/bootstrap.php`:

    Configure::write('CA.Models.blogs', 'Blogs');

Now the magic has been done. Reload your admin-panel and you will see a new menu-item called 'Blogs'! When you click on
it, you are able to add blogs via the '+' button on the right. After adding blogs you are able to view, edit and delete
them. How nice is that?

Maybe you want to customize this PostType. For example, you would like to add form-fields, or remove some table-columns.
This is all possible by editing the PostType-array you added in your `BlogsModel`. Take a look at
[this page](/docs/cakeadmin/1.0/tutorials-and-examples/adding-posttypes) to learn more.

Done
----

Congratulations, you are done! You have installed the CakeAdmin Plugin, are known with its features, and extended the
admin-panel with your own PostType. There is a lot more to discover. For that, read the docs, discover
www.cakemanager.org and see our other plugins who extend the CakeAdmin Plugin.

Greetings,


Bob Mulder

The CakeManager Team

