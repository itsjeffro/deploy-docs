# Updating Deploy

To update you may run `composer update`.

```
composer update
```

## Updating assets and migrations

```
php artisan vendor:publish --tag=deploy-assets --force
```

Finally you may run the migrations to ensure all the deploy tables are up-to-date.

```
php artisan migrate
```
