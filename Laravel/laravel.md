# Laravel

## Table of Contents

1. [Introduction to Laravel](#introduction-to-laravel)
2. [Installation](#installation)
3. [Building a Laravel App](#building-a-laravel-app)

---

## Introduction to Laravel

Laravel is a PHP framework designed for web application development. It follows the MVC (Model-View-Controller) architectural pattern, which helps in creating efficient and robust web applications. It is a web application framework with expressive, elegant syntax.

Laravel strives to provide an amazing developer experience while offering powerful features such as thorough dependency injection, an expressive database abstraction layer, queues and scheduled jobs, unit and integration testing, and more.

---

## Installation

### Prerequisites

Before you install the latest version of Laravel, make sure you have the following:

- PHP >= 8.2
- Composer
- A web server like Apache or Nginx
- Database (MySQL, PostgreSQL, SQLite, etc.)

### Step-by-Step Installation

1. **Install XAMPP**

   Download and install XAMPP from [XAMPP's official website](https://www.apachefriends.org/download.html). This will fulfill most of the prerequisites.

2. **Install Composer**

   Composer is a dependency manager for PHP. You can install it globally by following the instructions on [Composer's official website](https://getcomposer.org/download/). 

   You can run the exe installer or use the CLI commands below.

   **Note**:
   - Set up PHP in the environment variable before using the CLI. (Refer to the detailed installation guide below.)

   ```sh
   php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
   php -r "if (hash_file('sha384', 'composer-setup.php') === 'dac665fdc30fdd8ec78b38b9800061b4150413ff2e3b6f88543c636f7cd84f6db9189d43a81e5503cda447da73c7e5b6') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
   php composer-setup.php
   php -r "unlink('composer-setup.php');"
   mv composer.phar /usr/local/bin/composer
   ```

   **Check Installation**

   ```sh
   php --version
   composer --version
   ```

   **Note**:
   - Set up Composer in the environment variable if a problem occurs even after restarting.

3. **Install Laravel**

   Use Composer to install Laravel globally.

   ```sh
   composer global require laravel/installer
   ```

   **Verify Install**
   ```sh
   laravel --version
   ```

   **Note**: You might need to make some modifications in `php.ini` inside `xampp/php`, such as enabling the zip extension for the project to work in XAMPP.

4. **Create Project**

   Navigate to the desired folder and run the following command in the terminal.

   ```sh
   laravel new firstwebsite
   ```

   You might need to setup extra parameters as well. You can choose your database as well after installation. Make sure you check the `env` file & make a database in `phpMyAdmin` accordingly before proceding.

5. **Navigate to the Project Directory**

   ```sh
   cd firstwebsite
   ```

   A sample website will be in the `public` folder.

   **To access it in the browser**:

   - Open XAMPP and start the Apache Server.
   - In your browser, navigate to `localhost/your_project_folder`.

   **Note**: You need to have your project inside the `htdocs` folder to use XAMPP.

---

## Building a Laravel App

### Step 1: Create a New Laravel Project

Navigate to the desired folder and enter the following command in the terminal.

```sh
laravel new laravel-project
cd laravel-project
```

### Step 2: Set Up Environment Variables

1. **Configure Database**

   Open the `.env` file and update your database configuration:

   ```env
   DB_CONNECTION=mysql
   DB_HOST=127.0.0.1
   DB_PORT=3306
   DB_DATABASE=your_database_name
   DB_USERNAME=your_database_username
   DB_PASSWORD=your_database_password
   ```

2. **Create a New Database**

   Ensure you have a new database created in phpMyAdmin with the proper names.

3. **Navigate to the Page**

   - Open XAMPP and start the Apache Server.
   - In your browser, navigate to `localhost/your_project_folder`.

---

## Additional Resources

- [Laravel Documentation](https://laravel.com/docs)
- [Laracasts](https://laracasts.com)
- [Laravel Setup Tutorial](https://youtu.be/iBaM5LYgyPk?si=378JQf3-lo-nGLXh&t=0)
