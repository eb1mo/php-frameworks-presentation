

# Laravel Presentation

## Table of Contents
1. [Introduction to Laravel](#introduction-to-laravel)
2. [Installation](#installation)
3. [Building Your First Laravel App](#building-your-first-laravel-app)

---

## Introduction to Laravel

Laravel is a PHP framework designed for web application development. It follows the MVC (Model-View-Controller) architectural pattern, which helps in creating efficient and robust web applications.

### Features of Laravel:
- **Eloquent ORM**: An advanced ActiveRecord implementation for working with your database.
- **Blade Templating Engine**: Simple yet powerful templating engine.
- **Routing**: A simple and elegant way to define routes.
- **Middleware**: Filter HTTP requests entering your application.
- **Authentication**: Pre-built authentication system.

---

## Installation

### Prerequisites
Before you install Laravel, make sure you have the following:
- PHP >= 7.3
- Composer
- A web server like Apache or Nginx
- Database (MySQL, PostgreSQL, SQLite, etc.)

### Step-by-Step Installation

1. **Install Composer**:
    Composer is a dependency manager for PHP. You can install it globally by following the instructions on [Composer's official website](https://getcomposer.org/download/).

    ```sh
    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    php composer-setup.php
    php -r "unlink('composer-setup.php');"
    mv composer.phar /usr/local/bin/composer
    ```

2. **Install Laravel**:
    Use Composer to create a new Laravel project.

    ```sh
    composer create-project --prefer-dist laravel/laravel my-first-app
    ```

3. **Navigate to the project directory**:
    ```sh
    cd my-first-app
    ```

4. **Run the Laravel development server**:
    ```sh
    php artisan serve
    ```

    This command will start a local development server at `http://localhost:8000`.

---

## Building Your First Laravel App

Let's build a simple task list application to get you started with Laravel.

### Step 1: Create a New Laravel Project
If you haven't created a new Laravel project yet, do so by running:
```sh
composer create-project --prefer-dist laravel/laravel task-list-app
cd task-list-app
```

### Step 2: Set Up Database
1. **Configure Environment Variables**:
    Open the `.env` file and update your database configuration:
    ```env
    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3306
    DB_DATABASE=your_database_name
    DB_USERNAME=your_database_username
    DB_PASSWORD=your_database_password
    ```

2. **Create a new database**:
    Ensure you have a new database created. You can use tools like phpMyAdmin or command line to create a new database.

### Step 3: Create a Model and Migration
1. **Generate a model and migration for Task**:
    ```sh
    php artisan make:model Task -m
    ```

2. **Define the table schema**:
    Open the generated migration file in `database/migrations` and define the columns:

    ```php
    public function up()
    {
        Schema::create('tasks', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->boolean('completed')->default(false);
            $table->timestamps();
        });
    }
    ```

3. **Run the migration**:
    ```sh
    php artisan migrate
    ```

### Step 4: Create a Controller
1. **Generate a controller for Task**:
    ```sh
    php artisan make:controller TaskController
    ```

2. **Define basic CRUD operations**:
    Open the generated controller in `app/Http/Controllers/TaskController.php` and add the following code:

    ```php
    <?php

    namespace App\Http\Controllers;

    use App\Models\Task;
    use Illuminate\Http\Request;

    class TaskController extends Controller
    {
        public function index()
        {
            $tasks = Task::all();
            return view('tasks.index', compact('tasks'));
        }

        public function create()
        {
            return view('tasks.create');
        }

        public function store(Request $request)
        {
            $request->validate([
                'name' => 'required'
            ]);

            Task::create($request->all());

            return redirect()->route('tasks.index')
                             ->with('success', 'Task created successfully.');
        }

        public function edit(Task $task)
        {
            return view('tasks.edit', compact('task'));
        }

        public function update(Request $request, Task $task)
        {
            $request->validate([
                'name' => 'required'
            ]);

            $task->update($request->all());

            return redirect()->route('tasks.index')
                             ->with('success', 'Task updated successfully.');
        }

        public function destroy(Task $task)
        {
            $task->delete();

            return redirect()->route('tasks.index')
                             ->with('success', 'Task deleted successfully.');
        }
    }
    ```

### Step 5: Define Routes
1. **Add resource routes**:
    Open `routes/web.php` and add:

    ```php
    Route::resource('tasks', TaskController::class);
    ```

### Step 6: Create Views
1. **Create the necessary views**:
    - `resources/views/tasks/index.blade.php`
    - `resources/views/tasks/create.blade.php`
    - `resources/views/tasks/edit.blade.php`

    Here is an example for `index.blade.php`:
    ```php
    @extends('layouts.app')

    @section('content')
        <div class="container">
            <h1>Task List</h1>
            <a href="{{ route('tasks.create') }}" class="btn btn-primary">Add Task</a>
            <table class="table table-bordered mt-3">
                <thead>
                    <tr>
                        <th>ID</th>
                        <th>Name</th>
                        <th>Completed</th>
                        <th>Actions</th>
                    </tr>
                </thead>
                <tbody>
                    @foreach ($tasks as $task)
                        <tr>
                            <td>{{ $task->id }}</td>
                            <td>{{ $task->name }}</td>
                            <td>{{ $task->completed ? 'Yes' : 'No' }}</td>
                            <td>
                                <a href="{{ route('tasks.edit', $task->id) }}" class="btn btn-warning">Edit</a>
                                <form action="{{ route('tasks.destroy', $task->id) }}" method="POST" style="display:inline;">
                                    @csrf
                                    @method('DELETE')
                                    <button type="submit" class="btn btn-danger">Delete</button>
                                </form>
                            </td>
                        </tr>
                    @endforeach
                </tbody>
            </table>
        </div>
    @endsection
    ```

    Similar templates can be created for `create.blade.php` and `edit.blade.php`.

---

## Conclusion
By following the steps above, you can set up a basic Laravel application and build a simple task list app. This should give you a solid foundation to explore more advanced features of Laravel.

Feel free to explore the [Laravel documentation](https://laravel.com/docs) for more information and advanced topics.

---

## Additional Resources
- [Laravel Documentation](https://laravel.com/docs)
- [Laracasts](https://laracasts.com)
- [Laravel News](https://laravel-news.com)

---
```

You can copy this markdown content into a README.md file and host it on your GitHub repository.

---

***Handling multiple papers?*** 

Speed up your research with Sider! Our AI-powered sidebar features 10+ one-click tools including a more advanced Search Agent, ChatPDF, context-aware utilities and more to help you work smarter and faster.
 [Level up your research game here](https://bit.ly/4aSnMXa)
