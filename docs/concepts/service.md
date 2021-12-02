---
sidebar_position: 1
---

# Service

## Generate a new service
You may generate a new service directory by using the following command

```shell
php artisan bit.service:make Admin
```

After the command line executes successfully, a folder named `Admin` will be created in the path `app/Services`.

```
app/
└── Services/
    └── Admin/
        ├── Features
        ├── Http/
        │   ├── Controllers
        │   └── Middlewares
        ├── Providers/
        │   ├── AdminServiceProvider.php
        │   └── RouteServiceProvider.php
        └── routes/
            ├── api.php
            └── web.php
```

## Register a service
Services that have been successfully created do not automatically enroll them in your application. So you need to manually register them if you want to use them.

### Via configuration
In `config/app.php` configuration file, you may declare the Service Provider class of the service that you want to register.

```php title="config/app.php"
'providers' => [
    \App\Services\Providers\AdminServiceProvider::class,
]
```
### Via other Service Provider
You may register it in any Service Provider that registered in your application, such as `App\Providers\AppServiceProvider`.

```php title="app/Providers/AppServiceProvider.php"
use App\Services\Providers\AdminServiceProvider;

public function register()
{
    $this->app->register(AdminServiceProvider::class);
}
```

With this way, you may register a service dynamically with any condition.
```php title="app/Providers/AppServiceProvider.php"
use App\Services\Providers\AdminServiceProvider;
use Illuminate\Support\Facades\App;

public function register()
{
    if (App::environment('local')) {
        $this->app->register(AdminServiceProvider::class);
    }
}
```

## List all services
You may see all services in your application via the following command.

```shell
php artisan bit.service:list
```

## Delete a service
You may also delete specified service with the given name by the following command.

```shell
php artisan bit.service:delete Admin
```

