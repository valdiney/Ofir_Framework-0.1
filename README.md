# Ofir_Framework-0.1

# Description
Welcome to Ofir. This is a Project Development of the PHP-Framework. Developed of  student to students. What do you think about contribute with this project?

<p>
The Ofir is very easy to use. You just need instal and run in your server.
Ofir uses the Model-View-Controller approach, which allows great separation between logic and presentation. 
</p>

# What I need at this moment?
I need to create a powerful class to work with SQL query. My objective is abstracting the SQL language in the Application.

<h4>Exemple of the Model class</h4>
````php

class User extends Model
{
    protected $table = 'user';
}

```

<h3>Exemple of the Controller class</h3>

````php

class User_Controller extends Controller 
{
    protected $user;
    protected $view;
    protected $default_layout;

    public function __construct(Array $models, Array $services)
    {
        $this->user = $models['User'];
        $this->view = $this->view();
        $this->default_layout = $this->view->layout('default_layout');
    }

    public function index()
    {
        $this->default_layout

        $users = $this->user->select()->get_all();
        return $this->view->make('home.index', compact('users'));
    }
}

```
<h3>Exemple of the View</h3>

````php

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>User Page</title>
</head>
<body>
    <?php foreach ($users as $user):?>
       <b>Name:</b> <?php $user->name;?> <br>
       <b>Email:</b> <?php $user->email;?> <br>
    <?php endforeach;?>
</body>
</html>

```
