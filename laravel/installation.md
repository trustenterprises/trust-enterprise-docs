---
description: How to install and migrate the database.
---

# Installation

## Installation:

The Laravel Package is hosted on [Packagist](https://packagist.org/packages/trustenterprises/hashgraph). Install as below.

```
composer require trustenterprises/hashgraph
```

### Requirements

* PHP 7.4
* Laravel 7.\*

This package will have releases that will support Laravel 5.8.\* projects, the version of Guzzle needed to be lowered to meet these requirements.

## Database migration

Run these commands in your terminal to publish and migrate your new tables.

```
php artisan vendor:publish --provider="Trustenterprises\LaravelHashgraph\LaravelHashgraphServiceProvider" --tag="migrations"
php artisan migrate
```

## Configuration

Publish your config file with this command.

```
php artisan vendor:publish --provider="Trustenterprises\LaravelHashgraph\LaravelHashgraphServiceProvider" --tag="config"
```

## Adding your Environment Variables

Update these environment variables in your **.env** file with your client URL and secret key.

* HASHGRAPH\_NODE\_URL
* HASHGRAPH\_SECRET\_KEY

Don't forget to reset your server to update the config.

## Updating the webhook route

By default the callback webhook route in the app ends with **/hashgraph** this can be changed by updating the **HASHGRAPH\_WEBHOOK\_ROUTE** in your Laravel App.
