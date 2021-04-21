# Development

## Getting started

Clone the package into the project root.

```bash
git clone https://github.com/itsjeffro/deploy.git
```

### Composer dependencies

Add the following to your main Laravel project's composer.json and then run `composer require itsjeffro/deploy`.

```json
{
    "repositories": [ 
        {
            "type": "path",
            "url": "deploy",
            "options": {
                "symlink": true
            }
        } 
    ]
}
```

### NPM dependencies

Run `npm install` to install any frontend dependencies.

## Working on the Frontend

Compiled assets will be automatically copied over to the main project's public directory as `vendor/deploy`. If it does not, then you may not have cloned the package to the correct path in your project.

### Compiling assets

While working on the frontend related files, you may run `npm run watch`.

Prior to pushing changes to the repository, you must run `npm run prod` so that everything is minified etc.

## Working on the API

TBA

## Tests

To ensure no features are broken, the following can be run using `phpunit`. Since integration tests are inlcuded, a database will be required.

```bash
cp phpunit.xml.dist phpunit.xml
```

Next, update the env values to reflect the database you will be running migrations and tests against. The database used is `deploy_test` during the setup.

### Running without coverage

```bash
./vendor/bin/phpunit
```

### Running with coverage

```bash
./vendor/bin/phpunit --coverage-html coverage
```