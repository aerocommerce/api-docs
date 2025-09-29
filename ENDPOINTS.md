## Endpoints

### Orders

| URL                         | Permission          | Action | Examples                                          | Purpose                                    |
|-----------------------------|---------------------|--------|---------------------------------------------------|--------------------------------------------|
| /api/orders/                | orders.index        | GET    | [Order Index](Examples/Order/INDEX.md)            | Get all orders (paginated)                 |
| /api/orders/{id}            | orders.view         | GET    | [View Order](Examples/Order/VIEW.md)              | Get an order by id                         |
| /api/orders                 | orders.store        | POST   | [Store Order](Examples/Order/STORE.md)            | Create an order from json data             |
| /api/orders/{id}/flags/{id} | orders.flags.store  | POST   | [Store Order Flag](Examples/Order/FLAGS.md)       | Attach a flag to an order from json data   |
| /api/orders/{id}/flags/{id} | orders.flags.delete | DELETE | [Delete Order Flag](Examples/Order/FLAGS.md)      | Detach a flag from an order from json data |
| /api/orders/{id}/comments   | orders.flags.store  | POST   | [Store Order Comment](Examples/Order/COMMENTS.md) | Add an order to an order from json data    |

**NOTE:** Passing a `reference` in place of an `id` is supported for all relevant order endpoints, e.g. `/api/orders/REF-123`

**NOTE:** Passing a `name` in place of an `id` is supported for the order flag endpoints, e.g. `/api/orders/REF-123/flags/name`

### Fulfillments

| URL                                | Permission          | Action  | Examples                                             | Purpose                                          |
|------------------------------------|---------------------|---------|------------------------------------------------------|--------------------------------------------------|
| /api/orders/{id}/fulfillments      | fulfillments.store  | POST    | [Store Fulfillment](Examples/Fulfillment/STORE.md)   | Create a fulfillment for an order from json data |
| /api/orders/{id}/fulfillments/{id} | fulfillments.delete | DELETE  | [Delete Fulfillment](Examples/Fulfillment/DELETE.md) | Delete (cancel) a fulfillment for an order       |

**NOTE:**: Passing a `reference` in place of an `id` is supported (for both the order & the fulfillment)

### Order Statuses

| URL                      | Permission            | Action | Examples                                             | Purpose                            |
|--------------------------|-----------------------|--------|------------------------------------------------------|------------------------------------|
| /api/order-statuses      | order-statuses.index  | GET    | [Order Status Index](Examples/OrderStatus/INDEX.md)  | Get all order statuses (paginated) |
| /api/order-statuses/{id} | order-statuses.view   | GET    | [View Order Status](Examples/OrderStatus/VIEW.md)    | Get order status by id             |

### Products

| URL                  | Permission      | Action | Examples                                       | Purpose                         |
|----------------------|-----------------|--------|------------------------------------------------|---------------------------------|
| /api/products        | products.index  | GET    | [Product Index](Examples/Product/INDEX.md)     | Get all products (paginated)    |
| /api/products/search | products.search | GET    | [Product Search](Examples/Product/SEARCH.md)   | Search all products (paginated) |
| /api/products/{id}   | products.view   | GET    | [View Product](Examples/Product/VIEW.md)       | Get product by id               | 
| /api/products        | products.store  | POST   | [Store Product](Examples/Product/STORE.md)     | Create a product from json data | 
| /api/products/{id}   | products.store  | PUT    | [Update Product](Examples/Product/UPDATE.md)   | Update a product from json data |

**NOTE:** The `view` and `update` product routes support passing the product's `model` instead of the `id`, e.g. `/api/products/model`

**NOTE:** The `/api/products/search` exists to allow filtering at elasticsearch document level rather than eloquent level

### Variants

| URL                              | Permission      | Action | Examples                                     | Purpose                         |
|----------------------------------|-----------------|--------|----------------------------------------------|---------------------------------|
| /api/products/{id}/variants      | variants.store  | POST   | [Store Variant](Examples/Variant/STORE.md)   | Create a variant from json data |
| /api/products/{id}/variants/{id} | variants.update | PUT    | [Update Variant](Examples/Variant/UPDATE.md) | Update a variant from json data |

**NOTE:** The `update` variant route supports passing the variant's `sku` instead of the `id`, e.g. `/api/products/model/variants/sku`

### Manufacturers

| URL                     | Permission            | Action | Examples                                               | Purpose                              |
|-------------------------|-----------------------|--------|--------------------------------------------------------|--------------------------------------|
| /api/manufacturers      | manufacturers.index   | GET    | [Manufacturer Index](Examples/Manufacturer/INDEX.md)   | Get all manufacturers (paginated)    |
| /api/manufacturers/{id} | manufacturers.view    | GET    | [View Manufacturer](Examples/Manufacturer/VIEW.md)     | Get manufacturers by id              | 
| /api/manufacturers      | manufacturers.store   | POST   | [Store Manufacturer](Examples/Manufacturer/STORE.md)   | Create a manufacturer from json data | 
| /api/manufacturers/{id} | manufacturers.update  | PUT    | [Update Manufacturer](Examples/Manufacturer/UPDATE.md) | Update a manufacturer from json data |
| /api/manufacturers/{id} | manufacturers.delete  | DELETE | [Delete Manufacturer](Examples/Manufacturer/DELETE.md) | Delete a manufacturer                |

**NOTE:** Passing a `name` in place of an `id` is supported for all relevant manufacturer endpoints, e.g. `/api/manufacturers/burberry`

### Attribute Groups

| URL                         | Permission               | Action  | Examples                                                     | Purpose                                  |
|-----------------------------|--------------------------|---------|--------------------------------------------------------------|------------------------------------------|
| /api/attribute-groups       | attribute-groups.index   | GET     | [Attribute Group Index](Examples/AttributeGroup/INDEX.md)    | Get all attribute groups (paginated)     |
| /api/attribute-groups/{id}  | attribute-groups.view    | GET     | [View Attribute Group](Examples/AttributeGroup/VIEW.md)      | Get attribute groups by id               |
| /api/attribute-groups       | attribute-groups.store   | POST    | [Store Attribute Group](Examples/AttributeGroup/STORE.md)    | Create an attribute group from json data |
| /api/attribute-groups/{id}  | attribute-groups.update  | PUT     | [Update Attribute Group](Examples/AttributeGroup/UPDATE.md)  | Update an attribute group from json data |
| /api/attribute-groups/{id}  | attribute-groups.delete  | DELETE  | [Delete Attribute Group](Examples/AttributeGroup/DELETE.md)  | Delete an attribute group                |

**NOTE:** Passing a `name` in place of an `id` is supported for all relevant attribute group endpoints, e.g. `/api/attribute-groups/size`

### Attributes

| URL                                         | Permission         | Action  | Examples                                          | Purpose                             |
|---------------------------------------------|--------------------|---------|---------------------------------------------------|-------------------------------------|
| /api/attribute-groups/{id}/attributes       | attributes.store   | POST    | [Store Attribute](Examples/Attribute/STORE.md)    | Create an attribute from json data  |
| /api/attribute-groups/{id}/attributes/{id}  | attributes.update  | PUT     | [Update Attribute](Examples/Attribute/UPDATE.md)  | Update an attribute from json data  |
| /api/attribute-groups/{id}/attributes/{id}  | attributes.delete  | DELETE  | [Delete Attribute](Examples/Attribute/DELETE.md)  | Delete an attribute                 |

**NOTE:** Passing a `name` in place of an `id` is supported for all relevant attribute endpoints, e.g. `/api/attribute-groups/size/attributes/small`

### Categories

| URL                   | Permission         | Action  | Examples                                        | Purpose                          |
|-----------------------|--------------------|---------|-------------------------------------------------|----------------------------------|
| /api/categories       | categories.index   | GET     | [Category Index](Examples/Category/INDEX.md)    | Get all categories (paginated)   |
| /api/categories/{id}  | categories.view    | GET     | [View Category](Examples/Category/VIEW.md)      | Get categories by id             |
| /api/categories       | categories.store   | POST    | [Store Category](Examples/Category/STORE.md)    | Create a category from json data |
| /api/categories/{id}  | categories.update  | PUT     | [Update Category](Examples/Category/UPDATE.md)  | Update a category from json data |
| /api/categories/{id}  | categories.delete  | DELETE  | [Delete Category](Examples/Category/DELETE.md)  | Delete a category                |

**NOTE:** Passing a `name` or `breadcrumb` in place of an `id` is supported for all relevant category endpoints, e.g. `/api/categories/mens>coats` or `/api/categories/coats`

### Tag Groups

| URL                   | Permission         | Action  | Examples                                         | Purpose                           |
|-----------------------|--------------------|---------|--------------------------------------------------|-----------------------------------|
| /api/tag-groups       | tag-groups.index   | GET     | [Tag Group Index](Examples/TagGroup/INDEX.md)    | Get all tag groups (paginated)    |
| /api/tag-groups/{id}  | tag-groups.view    | GET     | [View Tag Group](Examples/TagGroup/VIEW.md)      | Get tag groups by id              |
| /api/tag-groups       | tag-groups.store   | POST    | [Store Tag Group](Examples/TagGroup/STORE.md)    | Create a tag group from json data |
| /api/tag-groups/{id}  | tag-groups.update  | PUT     | [Update Tag Group](Examples/TagGroup/UPDATE.md)  | Update a tag group from json data |
| /api/tag-groups/{id}  | tag-groups.delete  | DELETE  | [Delete Tag Group](Examples/TagGroup/DELETE.md)  | Delete a tag group                |

**NOTE:** Passing a `name` in place of an `id` is supported for all relevant tag group endpoints, e.g. `/api/tag-groups/size`

### Tags

| URL                             | Permission   | Action  | Examples                              | Purpose                      |
|---------------------------------|--------------|---------|---------------------------------------|------------------------------|
| /api/tag-groups/{id}/tags       | tags.store   | POST    | [Store Tag](Examples/Tag/STORE.md)    | Create a tag from json data  |
| /api/tag-groups/{id}/tags/{id}  | tags.update  | PUT     | [Update Tag](Examples/Tag/UPDATE.md)  | Update a tag from json data  |
| /api/tag-groups/{id}/tags/{id}  | tags.delete  | DELETE  | [Delete Tag](Examples/Tag/DELETE.md)  | Delete a tag                 |

**NOTE:** Passing a `name` in place of an `id` is supported for all relevant tag endpoints, e.g. `/api/tag-groups/size`

### Collections

| URL                     | Permission           | Action   | Examples                                            | Purpose                            |
|-------------------------|----------------------|----------|-----------------------------------------------------|------------------------------------|
| /api/collections        | collections.index    | GET      | [Collection Index](Examples/Collection/INDEX.md)    | Get all collections (paginated)    |
| /api/collections/{id}   | collections.view     | GET      | [View Collection](Examples/Collection/VIEW.md)      | Get collections by id              |
| /api/collections        | collections.store    | POST     | [Store Collection](Examples/Collection/STORE.md)    | Create a collection from json data |
| /api/collections/{id}   | collections.update   | PUT      | [Update Collection](Examples/Collection/UPDATE.md)  | Update a collection from json data |
| /api/collections/{id}   | collections.delete   | DELETE   | [Delete Collection](Examples/Collection/DELETE.md)  | Delete a collection                |

**NOTE:** Passing a `name` in place of an `id` is supported for all relevant collection endpoints, e.g. `/api/collections/sale`

### Customers

| URL                   | Permission       | Action  | Examples                                       | Purpose                          |
|-----------------------|------------------|---------|------------------------------------------------|----------------------------------|
| /api/customers        | customers.index  | GET     | [Customer Index](Examples/Customer/INDEX.md)   | Get all customers (paginated)    |
| /api/customers/{id}   | customers.view   | GET     | [View Customer](Examples/Customer/VIEW.md)     | Get customer by id               | 
| /api/customers        | customers.store  | POST    | [Store Customer](Examples/Customer/STORE.md)   | Create a customer from json data | 
| /api/customers/{id}   | customers.update | PUT     | [Update Customer](Examples/Customer/UPDATE.md) | Update a customer from json data |

### Addresses

| URL                                | Permission       | Action | Examples                                     | Purpose                          |
|------------------------------------|------------------|--------|----------------------------------------------|----------------------------------|
| /api/customers/{id}/addresses      | addresses.store  | POST   | [Store Address](Examples/Address/STORE.md)   | Create an address from json data | 
| /api/customers/{id}/addresses/{id} | addresses.update | PUT    | [Update Address](Examples/Address/UPDATE.md) | Update an address from json data |
| /api/customers/{id}/addresses/{id} | addresses.delete | DELETE | [Delete Address](Examples/Address/UPDATE.md) | Delete an address                |

### Payment Methods

| URL                        | Permission              | Action  | Examples                                                   | Purpose                             |
|----------------------------|-------------------------|---------|------------------------------------------------------------|-------------------------------------|
| /api/payment-methods       | payment-methods.index   | GET     | [Payment Method Index](Examples/PaymentMethod/INDEX.md)    | Get all payment methods (paginated) |
| /api/payment-methods/{id}  | payment-methods.view    | GET     | [View Payment Method](Examples/PaymentMethod/VIEW.md)      | Get payment method by id            |

### Shipping Methods

| URL                         | Permission                 | Action  | Examples                                                  | Purpose                              |
|-----------------------------|----------------------------|---------|-----------------------------------------------------------|--------------------------------------|
| /api/shipping-methods       | shipping-methods.index     | GET     | [Shipping Method Index](Examples/ShippingMethod/INDEX.md) | Get all shipping methods (paginated) |
| /api/shipping-methods/{id}  | shipping-methods.view      | GET     | [View Shipping Method](Examples/ShippingMethod/VIEW.md)   | Get shipping method by id            |

### Locations

| URL                   | Permission          | Action  | Examples                                       | Purpose                          |
|-----------------------|---------------------|---------|------------------------------------------------|----------------------------------|
| /api/locations        | locations.index     | GET     | [Location Index](Examples/Location/INDEX.md)   | Get all locations (paginated)    |
| /api/locations/{id}   | locations.view      | GET     | [View Location](Examples/Location/VIEW.md)     | Get locations by id              | 
| /api/locations        | locations.store     | POST    | [Store Location](Examples/Location/STORE.md)   | Create a location from json data | 
| /api/locations/{id}   | locations.update    | PUT     | [Update Location](Examples/Location/UPDATE.md) | Update a location from json data |

**NOTE:** Passing a `name` in place of an `id` is supported for all relevant location endpoints, e.g. `/api/locations/name`

### Flags

| URL              | Permission   | Action | Examples                                 | Purpose                      |
|------------------|--------------|--------|------------------------------------------|------------------------------|
| /api/flags       | flags.index  | GET    | [Flag Index](Examples/Flag/INDEX.md)     | Get all flags (paginated)    |
| /api/flags/{id}  | flags.view   | GET    | [View Flag](Examples/Flag/VIEW.md)       | Get flags by id              | 
| /api/flags       | flags.store  | POST   | [Store Flag](Examples/Flag/STORE.md)     | Create a flag from json data | 
| /api/flags/{id}  | flags.update | PUT    | [Update Flag](Examples/Flag/UPDATE.md)   | Update a flag from json data |
| /api/flags/{id}  | flags.delete | DELETE | [Delete Flag](Examples/Flag/DELETE.md)   | Delete a flag                |

**NOTE:** Passing a `name` in place of an `id` is supported for all relevant flag endpoints, e.g. `/api/flags/name`

### Price Lists

| URL                   | Permission          | Action | Examples                                          | Purpose                            |
|-----------------------|---------------------|--------|---------------------------------------------------|------------------------------------|
| /api/price-lists      | price-lists.index   | GET    | [Price List Index](Examples/PriceList/INDEX.md)   | Get all price lists (paginated)    |
| /api/price-lists/{id} | price-lists.view    | GET    | [View Price List](Examples/PriceList/VIEW.md)     | Get price list by id               | 
| /api/price-lists      | price-lists.store   | POST   | [Store Price List](Examples/PriceList/STORE.md)   | Create a price list from json data | 
| /api/price-lists/{id} | price-lists.store   | PUT    | [Update Price List](Examples/PriceList/UPDATE.md) | Update a price list from json data |

### Price List Entries

| URL                                  | Permission                | Action | Examples                                                     | Purpose                                  |
|--------------------------------------|---------------------------|--------|--------------------------------------------------------------|------------------------------------------|
| /api/price-lists/{id}/entries        | price-list-entries.store  | POST   | [Store Price List Entry](Examples/PriceListEntry/STORE.md)   | Create a price list entry from json data |
| /api/price-lists/{id}/entries/{id}   | price-list-entries.update | PUT    | [Update Price List Entry](Examples/PriceListEntry/UPDATE.md) | Update a price list entry from json data |


[Back to contents](README.md#table-of-contents)
