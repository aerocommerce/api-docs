# Aero API Docs

## Table of contents

1. [Usage](#usage)
2. [API Conventions](CONVENTIONS.md)
3. [Endpoints](ENDPOINTS.md)
4. [Responses](RESPONSES.md)
5. Examples
   1. Order
      1. [Store](Examples/Order/STORE.md)
      2. [View](Examples/Order/VIEW.md)
   2. Order Status
      1. [Index](Examples/OrderStatus/INDEX.md)
      2. [View](Examples/OrderStatus/VIEW.md)
   3. Payment Method
      1. [Index](Examples/PaymentMethod/INDEX.md)
      2. [View](Examples/PaymentMethod/VIEW.md)
   4. Product
      1. [Index](Examples/Product/INDEX.md)
      2. [View](Examples/Product/VIEW.md)
   5. Shipping Method
      1. [Index](Examples/ShippingMethod/INDEX.md)
      2. [View](Examples/ShippingMethod/VIEW.md)

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
