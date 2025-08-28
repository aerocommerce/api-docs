# Aero API Docs

## Table of contents

1. [Usage](#usage)
2. [API Conventions](CONVENTIONS.md)
3. [Endpoints](ENDPOINTS.md)
4. [Responses](RESPONSES.md)
5. Examples
   1. Orders
      1. [Index](Examples/Order/INDEX.md)
      2. [View](Examples/Order/VIEW.md)
      3. [Store](Examples/Order/STORE.md)
   2. Order Statuses
      1. [Index](Examples/OrderStatus/INDEX.md)
      2. [View](Examples/OrderStatus/VIEW.md)
   3. Payment Methods
      1. [Index](Examples/PaymentMethod/INDEX.md)
      2. [View](Examples/PaymentMethod/VIEW.md)
   4. Products
      1. [Index](Examples/Product/INDEX.md)
      2. [Search](Examples/Product/SEARCH.md)
      3. [View](Examples/Product/VIEW.md)
      4. [Store](Examples/Product/STORE.md)
      5. [Update](Examples/Product/UPDATE.md)
   5. Variants
      1. [Store](Examples/Variant/STORE.md)
      2. [Update](Examples/Variant/UPDATE.md)
   6. Customers
       1. [Index](Examples/Customer/INDEX.md)
       2. [View](Examples/Customer/VIEW.md)
       3. [Store](Examples/Customer/STORE.md)
       4. [Update](Examples/Customer/UPDATE.md)
   7. Addresses
       1. [Create](Examples/Address/STORE.md)
       2. [Update](Examples/Address/UPDATE.md)
       3. [Delete](Examples/Address/DELETE.md)
   8. Shipping Methods
      1. [Index](Examples/ShippingMethod/INDEX.md)
      2. [View](Examples/ShippingMethod/VIEW.md)
   9. Price Lists
       1. [Index](Examples/PriceList/INDEX.md)
       2. [View](Examples/PriceList/VIEW.md)
       3. [Store](Examples/PriceList/STORE.md)
       4. [Update](Examples/PriceList/UPDATE.md)
   10. Price List Entries
       1. [Store](Examples/PriceListEntry/STORE.md)
       2. [Update](Examples/PriceListEntry/UPDATE.md)
6. [Extending the API](EXTENDING.md) 

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
