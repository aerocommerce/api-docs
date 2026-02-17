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
    2. Fulfillments
        1. [Store](Examples/Fulfillment/STORE.md)
        2. [Delete](Examples/Fulfillment/DELETE.md)
    3. Order Statuses
        1. [Index](Examples/OrderStatus/INDEX.md)
        2. [View](Examples/OrderStatus/VIEW.md)
    4. Payment Methods
        1. [Index](Examples/PaymentMethod/INDEX.md)
        2. [View](Examples/PaymentMethod/VIEW.md)
    5. Products
        1. [Index](Examples/Product/INDEX.md)
        2. [Search](Examples/Product/SEARCH.md)
        3. [View](Examples/Product/VIEW.md)
        4. [Store](Examples/Product/STORE.md)
        5. [Update](Examples/Product/UPDATE.md)
    6. Variants
        1. [Store](Examples/Variant/STORE.md)
        2. [Update](Examples/Variant/UPDATE.md)
    7. Manufacturers
        1. [Index](Examples/Collection/INDEX.md)
        2. [View](Examples/Collection/VIEW.md)
        3. [Store](Examples/Collection/STORE.md)
        4. [Update](Examples/Collection/UPDATE.md)
        5. [Delete](Examples/Collection/DELETE.md)
    8. Attribute Groups
        1. [Index](Examples/AttributeGroup/INDEX.md)
        2. [View](Examples/AttributeGroup/VIEW.md)
        3. [Store](Examples/AttributeGroup/STORE.md)
        4. [Update](Examples/AttributeGroup/UPDATE.md)
        5. [Delete](Examples/AttributeGroup/DELETE.md)
    9. Attributes
        1. [Store](Examples/Attribute/STORE.md)
        2. [Update](Examples/Attribute/UPDATE.md)
        3. [Delete](Examples/Attribute/DELETE.md)
    10. Categories
        1. [Index](Examples/Category/INDEX.md)
        2. [View](Examples/Category/VIEW.md)
        3. [Store](Examples/Category/STORE.md)
        4. [Update](Examples/Category/UPDATE.md)
        5. [Delete](Examples/Category/DELETE.md)
    11. Tag Groups
        1. [Index](Examples/TagGroup/INDEX.md)
        2. [View](Examples/TagGroup/VIEW.md)
        3. [Store](Examples/TagGroup/STORE.md)
        4. [Update](Examples/TagGroup/UPDATE.md)
        5. [Delete](Examples/TagGroup/DELETE.md)
    12. Tags
        1. [Store](Examples/Tag/STORE.md)
        2. [Update](Examples/Tag/UPDATE.md)
        3. [Delete](Examples/Tag/DELETE.md)
    13. Collections
        1. [Index](Examples/Collection/INDEX.md)
        2. [View](Examples/Collection/VIEW.md)
        3. [Store](Examples/Collection/STORE.md)
        4. [Update](Examples/Collection/UPDATE.md)
        5. [Delete](Examples/Collection/DELETE.md)
    14. Customers
        1. [Index](Examples/Customer/INDEX.md)
        2. [View](Examples/Customer/VIEW.md)
        3. [Store](Examples/Customer/STORE.md)
        4. [Update](Examples/Customer/UPDATE.md)
    15. Addresses
        1. [Create](Examples/Address/STORE.md)
        2. [Update](Examples/Address/UPDATE.md)
        3. [Delete](Examples/Address/DELETE.md)
    16. Shipping Methods
        1. [Index](Examples/ShippingMethod/INDEX.md)
        2. [View](Examples/ShippingMethod/VIEW.md)
    17. Locations
        1. [Index](Examples/Location/INDEX.md)
        2. [View](Examples/Location/VIEW.md)
        3. [Store](Examples/Location/STORE.md)
        4. [Update](Examples/Location/UPDATE.md)
    18. Flags
        1. [Index](Examples/Flag/INDEX.md)
        2. [View](Examples/Flag/VIEW.md)
        3. [Store](Examples/Flag/STORE.md)
        4. [Update](Examples/Flag/UPDATE.md)
        5. [Delete](Examples/Flag/DELETE.md)
    19. Price Lists
        1. [Index](Examples/PriceList/INDEX.md)
        2. [View](Examples/PriceList/VIEW.md)
        3. [Store](Examples/PriceList/STORE.md)
        4. [Update](Examples/PriceList/UPDATE.md)
    20. Price List Entries
        1. [Store](Examples/PriceListEntry/STORE.md)
        2. [Update](Examples/PriceListEntry/UPDATE.md)
    21. Specification Groups
        1. [Index](Examples/SpecificationGroup/INDEX.md)
        2. [View](Examples/SpecificationGroup/VIEW.md)
        3. [Store](Examples/SpecificationGroup/STORE.md)
        4. [Update](Examples/SpecificationGroup/UPDATE.md)
    22. Upsell Groups
        1. [Index](Examples/UpsellGroup/INDEX.md)
        2. [View](Examples/UpsellGroup/VIEW.md)
        3. [Store](Examples/UpsellGroup/STORE.md)
        4. [Update](Examples/UpsellGroup/UPDATE.md)
    23. Listing Collection Groups
        1. [Index](Examples/ListingCollectionGroup/INDEX.md)
        2. [View](Examples/ListingCollectionGroup/VIEW.md)
        3. [Store](Examples/ListingCollectionGroup/STORE.md)
        4. [Update](Examples/ListingCollectionGroup/UPDATE.md)
    24. Stock
        1. [Update](Examples/Stock/UPDATE.md)
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
