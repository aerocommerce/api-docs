# Aero API Docs

## Table of contents

1. [Installation](#installation)
2. [Usage](#usage)
3. [API Conventions](CONVENTIONS.md)
5. [Endpoints](ENDPOINTS.md)
4. [Responses](RESPONSES.md)
6. Payloads
   1. [Order](Payloads/Order)
      1. [Store](Payloads/Order/STORE.md)
   2. [Shipping Address]()
      1. [Store]()
   3. [Billing Address]()
       1. [Store]()
   4. [Order Items]()
      1. [Store]()

## Installation

```
composer require aerocommerce/api
```

This module requires the `api_tokens` & `api_usage_logs` tables, which can be created by migrating:

```
php artisan migrate --force
```

To ensure the API token generation is secure please define the secret used to create them in your auth config file, e.g.:

```php
{
    //...

    "jwt_secret" => "secret here"
}
```

## Usage

### Creating a token

To create a token navigate to `/admin/module/api-tokens/create`

To be secure it is recommended that you should only give the token the necessary permissions for its functionality and consider adding an expiry date

The permissions of a token can be edited at any time by navigating to `/admin/module/api-tokens/edit/{id}` but the expiry date can not

Once you have saved the API token you will be redirected and given **ONE** opportunity to copy the token

### Using a token

To use a token simply include it as a bearer token upon making an API request

### Deleting a token

For security reasons it is recommended to delete a token if it is no longer needed

This can be done using the `Delete API tokens` bulk action accessible by navigating to `/admin/module/api-tokens`

### Logging

Any request made to the API is logged, you can see the logs by navigating to `/admin/module/api-usage-logs`

Clicking into the logs you will be able to see the request and response data associated with it
