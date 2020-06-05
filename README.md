[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](http://badges.mit-license.org)
[![Build Status](https://travis-ci.org/Codexshaper/php-database.svg?branch=master)](https://travis-ci.org/Codexshaper/php-database)
[![StyleCI](https://github.styleci.io/repos/269548874/shield?branch=master)](https://github.styleci.io/repos/269548874)
[![Quality Score](https://img.shields.io/scrutinizer/g/Codexshaper/php-database.svg?style=flat-square)](https://scrutinizer-ci.com/g/Codexshaper/php-database)
[![Downloads](https://poser.pugx.org/Codexshaper/php-database/d/total.svg)](https://packagist.org/packages/Codexshaper/php-database)
[![Latest Version on Packagist](https://img.shields.io/packagist/v/Codexshaper/php-database.svg?style=flat-square)](https://packagist.org/packages/Codexshaper/php-database)

# Database and ORM
Laravel database and eloquent for php project.

## Download

```
composer require codexshaper/php-database
```

## Setup root facade

```
use Illuminate\Support\Facades\Facade;
use Illuminate\Container\Container;

Facade::setFacadeApplication(new Container);
```

Note: If you alraedy setup `container` as a root facade then leave it.

## Create a new connection
```
use CodexShaper\Database\Database;
```
### Using `constructor`
```
$db = new Database([
	"driver" 		=> "mysql",
	"host" 			=> 'localhost',
	"database" 		=> 'db_name',
	"username" 		=> 'db_user',
	"password" 		=> 'db_password',
	"prefix"   		=> 'db_prefix',
	"charset"   	=> 'utf8mb4',
	"collation"   	=> 'utf8mb4_unicode_ci',
]);
```
### Using `addConnection` method

```
$db = new Database;
$db->addConnection([
	"driver" 		=> "mysql",
	"host" 			=> 'localhost',
	"database" 		=> 'laravel-woocommerce',
	"username" 		=> 'root',
	"password" 		=> '',
	"prefix"   		=> 'wp_',
	"charset"   	=> 'utf8mb4',
	"collation"   	=> 'utf8mb4_unicode_ci',
]);
```

## Finaly `run` database to use globally and setup eloquent orm

```
$db->run();
```

## Create a table

```
use CodexShaper\Database\Facades\Schema;
use Illuminate\Database\Schema\Blueprint;

Schema::create('users', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->string('email')->unique();
    $table->timestamp('email_verified_at')->nullable();
    $table->string('password');
    $table->rememberToken();
    $table->timestamps();
});
```

## Drop a table

```
use CodexShaper\Database\Facades\Schema;
Schema::dropIfExists('custom_options');
```
