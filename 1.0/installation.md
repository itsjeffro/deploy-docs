# Installation

## Requirements

- Laravel 5.8
- openssh-clients (installed on the servcer to establish ssh connections)

## Important notes

Given that the deployment process uses symlinks. The user performing the deployment actions will be required to have the ability to reload the php-fpm service on the server. You may create a deployment hook which does this after the "Clean Up" action.

See [folder structure](folder-structure.md) for more information.

## Installing Deploy

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

Run the package's migrations:

```
php artisan migrate
```

### Configuration

After publishing the assets, the primary config file will be located at `config/deploy.php`. 

Before using the deploy application, you will need to set up your repository provider and a proper queue driver.

### Available Providers

Update your `.env` file to include a provider of your choice. A minimum of one provider is required.

Ensure that the callback URL is set as well. For example, `yoursite.com/deploy/authorize/<provider>/access`.

#### Bitbucket

https://confluence.atlassian.com/bitbucket/oauth-on-bitbucket-cloud-238027431.html

```
BITBUCKET_OAUTH_KEY=client_id
BITBUCKET_OAUTH_SECRET=client_secret
```

Callback URL: `https://yoursite.com/deploy/authorize/bitbucket/access`

Permissions: `projects:read`, `account:read`, `webhooks:read and write`

#### Github

https://developer.github.com/apps/building-oauth-apps/creating-an-oauth-app/

```
GITHUB_OAUTH_KEY=client_id
GITHUB_OAUTH_SECRET=client_secret
```

Callback URL: `https://yoursite.com/deploy/authorize/github/access`

### Queue connection

In your `.env` file, `QUEUE_CONNECTION` should be changed to another connection other than "sync". This way the process workers can correctly work on the server hosting the deployment package. 

With the connection updated, paths such as  `/home/user/.ssh/known_hosts` will be used instead of `/var/www/.ssh/known_hosts`.

Worker roles also handle:

* Creating individual SSH private keys for each project`s server

* Handling deployments

* Managing the projects .env file

* Testing server connections

## Deploy dashboard

Once you have completed the bare minimum of installation, a dashboard to manage your projects will be exposed at `/deploy`.
