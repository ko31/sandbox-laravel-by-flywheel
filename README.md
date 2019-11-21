# Sandbox Laravel

This is sandbox Laravel development by Local by Flywheel.

- [Local by Flywheel \| Local WordPress development made simple](https://localbyflywheel.com/)

## Installation

Launch Local by Flywheel, and Add Local Site (Add `+` button).

- Site name: `Laravel`
- Environment: `Preffered`
- WordPress username and password: Anything(delete later)

Enable SSL on the dashboard.

- Local Sites > Laravel > SSL > Certificate > `TRUST`

Launch terminal, and download Laravel Installer.

```
$ composer global require laravel/installer
```

Set Laravel command path to environment variable.

```
$ vi ~/.bash_profile
export PATH=$PATH:$HOME/.composer/vendor/bin

$ source ~/.bash_profile
```

Delete `app` directory of local site.

```
$ cd ~/Local\ Sites/laravel/
$ rm -rf app
```

Install Laravel.

```
$ laravel new app
```

The Laravel `public` directory will be installed at the WordPress DocumentRoot location, as follows:

```
$ ls app
README.md		bootstrap		config			package.json		resources		storage			webpack.mix.js
app			composer.json		database		phpunit.xml		routes			tests
artisan			composer.lock		package-lock.json	public			server.php		vendor
```

Restart the site on the dashboard.

- Local Sites > Laravel > `STOP SITE` and `START SITE`

Visit https://laravel.local in your browser, you will see Laravel welcome page.

![](https://user-images.githubusercontent.com/84167/69327641-322fb500-0c91-11ea-8d26-57851cbc860d.png)

### DB Settings

Launch Adminer on the dashboard, delete all tables with the name `wp_`.

- Local Sites > Laravel > DATABASE > `ADMINER`

Refer to the DB information on the DATABASE tab of the dashboard. And Update the Laravel `.env` file.

```
DB_CONNECTION=mysql
DB_HOST=192.168.95.100
DB_PORT=4030
DB_DATABASE=local
DB_USERNAME=root
DB_PASSWORD=root
```

Move to `app` directory and migrate DB.

```
$ cd ~/Local\ Sites/laravel/app
$ php artisan migrate
```

If the message `Migration table created successfully.` is displayed, the database is ready.

### Mail Settings

Update the Laravel `.env` file for Mailhog settings.

```
MAIL_DRIVER=smtp
MAIL_HOST=localhost
MAIL_PORT=1025
```

### Auth Settings

Download package `laravel/ui`.

```
$ composer require laravel/ui --dev
```

Generate authentication scaffolding.

```
# Bootstrap
$ php artisan ui bootstrap --auth

# Vue
$ php artisan ui vue --auth

# React
$ php artisan ui react --auth
```

Install and build package using npm.

```
$ npm install && npm run dev
```

Visit https://laravel.local in your browser, you can register account.

![](https://user-images.githubusercontent.com/84167/69327652-35c33c00-0c91-11ea-9b37-4768c0bb49c9.png)
