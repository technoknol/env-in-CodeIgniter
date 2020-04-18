# Adding `.env` file (like laravel) support in CodeIgniter 
[![StyleCI](https://github.styleci.io/repos/212960577/shield?branch=master)](https://github.styleci.io/repos/212960577)

This is a showcase how you can implement Laravel like .env file structure in your CodeIgniter application, and make configurations easy for all the development, production, testing stages. You don't need to take care of `application/config/database.php` file each time you do `git pull` or put it in `.gitignore`. 


## Steps
##### 1. First add a package `vlucas/phpdotenv` via composer 
> Run `composer require vlucas/phpdotenv` command in your project root directory. (If you don't have composer.json, don't worry, composer will take care of it.
##### 2. Copy a file `Env.php` to your `application/libraries` directory.
> This will load your env file in environment.

If you are using `vulcas/phpdotenv` > `4`, then change code accordingly as mentioned in `Env.php` file.

##### 3. Copy `general_helper.php` to your `application/helpers` directory.
> This will add `env` helper method to get any variable stored in `.env` file.
##### 4. Autoload library 
> Add library to `$autoload['libraries']` like this 
```
$autoload['libraries'] = array('env');
```
##### 5. Autoload helper (application/config/autoload.php)
> Add helper to `$autoload['helper']` like this 
```
$autoload['helper'] = array('general');
```

##### 6. Autoload helper (application/config/autoload.php)
> Make `composer_autoload` to `vendor/autoload.php` file path like this in `config.php` file 
```
$config['composer_autoload'] = FCPATH. 'vendor'. DIRECTORY_SEPARATOR . 'autoload.php';
```
##### 7. Create an `.env` file
Create an `.env` file in your project root folder. 

##### 8. Access an env variable
> In your php code you can access any .env variable like below 
```
env('MY_VARIABLE');
```

Voila ! Now you can have multiple variables based on Environment, and don't need to manually change file and then put it in `.gitignore`.
