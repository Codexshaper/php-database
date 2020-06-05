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
