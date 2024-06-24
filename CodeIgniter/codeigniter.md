# CodeIgniter

## Table of Contents

1. [Introduction to CodeIgniter](#introduction-to-codeigniter)
2. [Installation](#installation)
3. [Building a CodeIgniter App](#building-a-codeigniter-app)

---

## Introduction to CodeIgniter

CodeIgniter is a powerful PHP framework with a very small footprint, built for developers who need a simple and elegant toolkit to create full-featured web applications. It is based on the MVC (Model-View-Controller) architectural pattern, which helps in creating efficient and robust web applications.

CodeIgniter is known for its speed and performance, offering features such as form and data validation, session management, and a rich set of libraries and helpers.

---

## Installation

### Prerequisites

Before you install the latest version of CodeIgniter, make sure you have the following:

- PHP >= 8.2
- Composer
- A web server like Apache or Nginx
- Database (MySQL, PostgreSQL, SQLite, etc.)
- Extensions like intl, mbstring, json

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
   php -r "if (hash_file('sha384', 'composer-setup.php') === 'aac92f1b92c54e7ea0dbbc85c6d85c818a3f9a98f0ea72a2b1676b74ff95b7cf') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
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

3. **Install CodeIgniter**

   Use Composer to install CodeIgniter.

   ```sh
   composer create-project codeigniter4/appstarter firstwebsite
   ```

   **Note**: You might need to make some modifications in `php.ini` inside `xampp/php`, such as enabling the `initl` extension for the project to work in XAMPP.

4. **Navigate to the Project Directory**

   ```sh
   cd firstwebsite
   ```

   A sample website will be in the `public` folder.

   **To access it in the browser**:

   - Open XAMPP and start the Apache Server.
   - In your browser, navigate to `localhost/firstwebsite/public`.

   **Note**: You need to have your project inside the `htdocs` folder to use XAMPP.

---

## Building a CodeIgniter App

### Step 1: Create a New CodeIgniter Project

Navigate to the desired folder and enter the following command in the terminal.

```sh
composer create-project codeigniter4/appstarter codeigniter-project
cd codeigniter-project
```

### Step 2: Set Up Environment Variables

1. **Configure Database**

   Open the `.env` file and update your database configuration:

   ```env
   database.default.hostname = localhost
   database.default.database = your_database_name
   database.default.username = your_database_username
   database.default.password = your_database_password
   database.default.DBDriver = MySQLi
   ```

2. **Create a New Database**

   Ensure you have a new database created in phpMyAdmin with the proper names.

3. **Navigate to the Page**

   - Open XAMPP and start the Apache Server.
   - In your browser, navigate to `localhost/codeigniter-project/public`.

---

## Additional Resources

- [CodeIgniter Documentation](https://www.codeigniter.com/user_guide/index.html)