PostTypes Component
===================

The PostTypes Component handles the PostTypes inside the CakeAdmin Panel.

[doc_toc]

Loading
-------

You can load the component in your AppController:

public function initialize() {
    $this->loadComponent('CakeAdmin.PostTypes');
}

> Note: The PostTypes Component is default loaded on CakeAdmin related Controllers.

Configuring
-----------

### Table

Under the `table`-configuration you are able to change the default configurations for the PostType tables. When the
PostType does not have information about how to generate the table (index-action), the Component will build the table
himself. However, there are default fields who are ignored. This can be changed via:

    $this->PostTypes->config('table.ignoredColumns', [
        'my-list',
        'of-ignored',
        'columns'
    ]);

Also you can change the maximum of fields to add to the table:

    $this->PostTypes->config('table.max', 4); // value is default set to 2

### Form
Under the `form`-configuration you are able to change the default configurations for the PostType forms - used for add
and edit actions. This configuration has also ignored fields, which can be changed this way:

    $this->PostTypes->config('form.ignoredFields', [
        'my-list',
        'of-ignored',
        'fields'
    ]);

Usage
-----

The PostTypes Component is used inside the CakeAdmin Panel. The component is used to register, modify and read
PostTypes. You cannot register PostTypes when you use the component in your own application, because your own
`AppController` is not used on CakeAdmin related requests. However, you are still able to get information if you want,
and via events you are able to trigger the PostTypes.


### Register
You can register PostTypes via the `register`-method. For example:

The following options are available to set, and get:

#### Model
The name of the model. For example `Blogs` or `Cms.Blogs`.

    $this->PostTypes->register('Blogs', [
        'model' => 'Blogs'
    ]);

> Note: Default, the model, added as first parameter to `register()` is used.

#### Menu
Boolean if the PostType should be added to the menu. Default `true`.

    $this->PostTypes->register('Blogs', [
        'menu' => false
    ]);

#### MenuWeight`
Integer of the height of the item in the whole menu. Default `20`.

    $this->PostTypes->register('Blogs', [
        'menuWeight' => 15
    ]);

#### Slug
Slug of the PostType. Automatically generated. If you really want to change the slug:

    $this->PostTypes->register('Blogs', [
        'slug' => 'my-blog'
    ]);

#### Name
Name of the PostType. Automatically generated. So `Blogs` will result in... Yeah... `Blogs` ;)

    $this->PostTypes->register('Blogs', [
        'name' => 'My awesome blogs!'
    ]);

#### Alias and AliasLc
Alias (humanized name) of the PostType. Automatically generated.
`aliasLc` is the same, only lowercased.

#### SingularAlias and SingularAliasLc
Alias (humanized name, in singular form) of the PostType. Automatically generated.
`singularAliasLc` is the same, only lowercased.

#### Description
Description of the PostType. Default `null`. This can be helpfull to provide other developers with some info about your
PostType.

    $this->PostTypes->register('Blogs', [
        'description' => 'This PostType manages all blogs, posted on this website.'
    ]);

#### Actions
Array with actions as key and bool as value to enable or disable actions. Default all actions are enabled.
Example to disable the delete-action, and enable the edit-action:

    $this->PostTypes->register('Blogs', [
        'actions' => [
            'delete' => false,
            'edit' => true,
        ]
    ]);

> Note: Default all actions are enabled.

#### Filters
Array of filters to use (SearchComponent of the Utils-plugin). For example:

    $this->PostTypes->register('Blogs', [
        'filters' => [
            'title',
            'state' => [
                'type' => 'select',
                'options' => [0 => 'Concept', 1 => 'Published']
            ]
        ]
    ]);

In this example there will be a input-field called `title` where there will be filtered on the title-column, and there
will be an select-box where you can select if you want concepts or published blogs.

> Note: Read more about filters [here](/docs/utils/1.0/components/search).

#### Query
Custom closure to customize your queries. This gives you te ability to use your own customized queries for finding
PostType data. Example:

    $this->PostTypes->register('Blogs', [
        'query' => function($query) {
            $query->contain('Categories');

            return $query;
        }
    ]);

#### TableColumns
Automatically, some columns are selected to show on the 'index'-action of your PostType. You can configure your own
selection by changing the `tableColumns`-key of the PostTypes configs. Look at this example:

    public function postType() {
        return [
            'tableColumns' => [
                'id',
                'name',
                'category_id' => [
                    'get' => 'category.name'
                ],
                'created_by',
                'modified_by',
            ]
        ];
    }

This is your own selection of columns to show on your 'index'-action.

#### FormFields
Automatically, some fields are selected to show on the `add`- and `edit`-action of your PostType. You can configure your
own selection by changing the `formFields`-key of the PostTypes configs. Look at this example:

    public function postType() {
        return [
            'formFields' => [
                'id',
                'name' => [
                    'type' => 'input',
                    'error' => 'Failure!'
                ],
                'country' => [
                    'default' => 'The Netherlands'
                ],
                'created_by' => [
                    'label' => 'creator'
                ],
                'modified_by',
            ]
        ];
    }

### GetOption
With the method `getOption()` you are able to get options from specific PostTypes. For example:

    // will return all options of the PostType blogs
    $this->PostTypes->getOption('blogs');

    // will return the description of the PostType blogs
    $this->PostTypes->getOption('blogs', 'description');