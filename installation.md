# Installation

## Requirements

- Laravel 7.0+
- openssh-clients (installed on the server to establish ssh connections)

## Important notes

### PHP projects

Due to the use of symbolic links (symlinks), the SSH user performing server actions should be able to run `service php-fpm reload`. You may create a deployment hook which does this after the "Clean Up" action.

## Installing Deploy

Prior to installing this package, it is assumed you have already configured an auth guard with the App\User model for your Laravel application. 

Using composer, install the package into your Laravel project:

```bash
composer require itsjeffro/deploy
```

The package will automatically register its service provider.

Publish the package's config and assets:

```bash
php artisan vendor:publish --tag=deploy-config
php artisan vendor:publish --tag=deploy-assets
```

Run the package's migrations:

```bash
php artisan migrate
```

### Configuration

After publishing the assets, the primary config file will be located at `config/deploy.php`. Before using the deploy application, you will need to set up your repository provider and a proper queue driver.

#### Repository providers

Update your `.env` file to include a provider of your choice. A minimum of one provider is required.

See [repository providers](repository-providers.md) for more information.

#### Queue connection

In your `.env` file, `QUEUE_CONNECTION` should be changed to another connection other than "sync". This way the process workers can correctly work on the server hosting the deployment package. 

With the connection updated, paths such as  `/home/user/.ssh/known_hosts` will be used instead of `/var/www/.ssh/known_hosts`.

Worker roles also handle:

- Creating individual SSH private keys for each project`s server

- Handling deployments

- Managing the projects .env file

- Testing server connections

## Deploy dashboard

Once you have completed the bare minimum of installation, a dashboard to manage your projects will be exposed at `/deploy`.
