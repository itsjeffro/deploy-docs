# Installation

## Requirements

- Laravel 5.8
- openssh-clients (installed on the servcer to establish ssh connections)

## Installing this package

Prior to installing this package, it is assumed you have already configured an auth gaurd with the App\User model for your Laravel application. 

Using composer, install the package into your Laravel project:

```
composer require itsjeffro/deploy
```

The package will automatically register its service provider.

Publish the package's config and assets:

```
php artisan vendor:publish --tag=deploy-config
php artisan vendor:publish --tag=deploy-assets
```

When you update to a new release of deploy package, you should make sure you update the assets using the command below.

```
php artisan vendor:publish --tag=deploy-assets --force
```

Run the package's migrations:

```
php artisan migrate
```
