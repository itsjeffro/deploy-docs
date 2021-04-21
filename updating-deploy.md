# Updating Deploy

To update you may run `composer update`.

```bash
composer update
```
Also, to ensure that the queue workers have the recent file changes you may run `php artisan queue:restart`.

```bash
php artisan queue:restart
```

## Updating assets and migrations

```bash
php artisan vendor:publish --tag=deploy-assets --force
```

Finally you may run the migrations to ensure all the deploy tables are up-to-date.

```bash
php artisan migrate
```
