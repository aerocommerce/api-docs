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
       4. [Flags](Examples/Order/FLAGS.md)
       5. [Comments](Examples/Order/COMMENTS.md)
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
   6. Manufacturers
       1. [Index](Examples/Collection/INDEX.md)
       2. [View](Examples/Collection/VIEW.md)
       3. [Store](Examples/Collection/STORE.md)
       4. [Update](Examples/Collection/UPDATE.md)
       5. [Delete](Examples/Collection/DELETE.md)
   7. Attribute Groups
       1. [Index](Examples/AttributeGroup/INDEX.md)
       2. [View](Examples/AttributeGroup/VIEW.md)
       3. [Store](Examples/AttributeGroup/STORE.md)
       4. [Update](Examples/AttributeGroup/UPDATE.md)
       5. [Delete](Examples/AttributeGroup/DELETE.md)
   8. Attributes
       1. [Store](Examples/Attribute/STORE.md)
       2. [Update](Examples/Attribute/UPDATE.md)
       3. [Delete](Examples/Attribute/DELETE.md)
   9. Categories
       1. [Index](Examples/Category/INDEX.md)
       2. [View](Examples/Category/VIEW.md)
       3. [Store](Examples/Category/STORE.md)
       4. [Update](Examples/Category/UPDATE.md)
       5. [Delete](Examples/Category/DELETE.md)
   10. Tag Groups
       1. [Index](Examples/TagGroup/INDEX.md)
       2. [View](Examples/TagGroup/VIEW.md)
       3. [Store](Examples/TagGroup/STORE.md)
       4. [Update](Examples/TagGroup/UPDATE.md)
       5. [Delete](Examples/TagGroup/DELETE.md)
   11. Tags
       1. [Store](Examples/Tag/STORE.md)
       2. [Update](Examples/Tag/UPDATE.md)
       3. [Delete](Examples/Tag/DELETE.md)
   12. Collections
       1. [Index](Examples/Collection/INDEX.md)
       2. [View](Examples/Collection/VIEW.md)
       3. [Store](Examples/Collection/STORE.md)
       4. [Update](Examples/Collection/UPDATE.md)
       5. [Delete](Examples/Collection/DELETE.md)
   13. Customers
       1. [Index](Examples/Customer/INDEX.md)
       2. [View](Examples/Customer/VIEW.md)
       3. [Store](Examples/Customer/STORE.md)
       4. [Update](Examples/Customer/UPDATE.md)
   14. Addresses
       1. [Create](Examples/Address/STORE.md)
       2. [Update](Examples/Address/UPDATE.md)
       3. [Delete](Examples/Address/DELETE.md)
   15. Shipping Methods
       1. [Index](Examples/ShippingMethod/INDEX.md)
       2. [View](Examples/ShippingMethod/VIEW.md)
   16. Flags
       1. [Index](Examples/Flag/INDEX.md)
       2. [View](Examples/Flag/VIEW.md)
       3. [Store](Examples/Flag/STORE.md)
       4. [Update](Examples/Flag/UPDATE.md)
       5. [Delete](Examples/Flag/DELETE.md)
   17. Price Lists
       1. [Index](Examples/PriceList/INDEX.md)
       2. [View](Examples/PriceList/VIEW.md)
       3. [Store](Examples/PriceList/STORE.md)
       4. [Update](Examples/PriceList/UPDATE.md)
   18. Price List Entries
       1. [Store](Examples/PriceListEntry/STORE.md)
       2. [Update](Examples/PriceListEntry/UPDATE.md)
6. [Extending the API](EXTENDING.md) 

## Usage

### Creating a token

To create a new API token, navigate to `/admin/module/api-tokens/create`

- Grant only the minimum permissions required for its purpose.
- Consider setting an expiry date for additional security.
- Token permissions can be edited at any time by visiting `/admin/module/api-tokens/edit/{id}` (expiry dates, once set, cannot be modified).

### Using a token

Include the token as a **Bearer token** in the `Authorization` header of your API requests

### Deleting a token

If a token is no longer needed, delete it for security reasons

This can be done using the `Delete API tokens` bulk action via `/admin/module/api-tokens`

### Logging

All API requests are logged by default (unless logging has been disabled in settings)

Logs can be viewed at: `/admin/module/api-usage-logs`

Clicking a log entry displays the full request and response data for debugging and auditing purposes
