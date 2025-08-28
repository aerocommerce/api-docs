## Endpoints

### Orders

| URL                         | Permission          | Action | Examples                                     | Purpose                                    |
|-----------------------------|---------------------|--------|----------------------------------------------|--------------------------------------------|
| /api/orders/                | orders.index        | GET    | [Order Index](Examples/Order/INDEX.md)       | Get all orders                             |
| /api/orders/{id}            | orders.view         | GET    | [View Order](Examples/Order/VIEW.md)         | Get an order by id                         |
| /api/orders                 | orders.store        | POST   | [Store Order](Examples/Order/STORE.md)       | Create an order from json data             |
| /api/orders/{id}/flags      | orders.flags.store  | POST   | [Store Order Flag](Examples/Order/FLAGS.md)  | Attach a flag to an order from json data   |
| /api/orders/{id}/flags/{id} | orders.flags.delete | DELETE | [Delete Order Flag](Examples/Order/FLAGS.md) | Detach a flag from an order from json data |

### Order Statuses

| URL                      | Permission            | Action | Examples                                             | Purpose                |
|--------------------------|-----------------------|--------|------------------------------------------------------|------------------------|
| /api/order-statuses      | order-statuses.index  | GET    | [Order Status Index](Examples/OrderStatus/INDEX.md)  | Get all order statuses |
| /api/order-statuses/{id} | order-statuses.view   | GET    | [View Order Status](Examples/OrderStatus/VIEW.md)    | Get order status by id | 

`/api/order-statuses` is paginated, see [Pagination Conventions](CONVENTIONS.md#pagination-conventions) for more info

### Products

| URL                  | Permission      | Action | Examples                                       | Purpose                         |
|----------------------|-----------------|--------|------------------------------------------------|---------------------------------|
| /api/products        | products.index  | GET    | [Product Index](Examples/Product/INDEX.md)     | Get all products                |
| /api/products/search | products.search | GET    | [Product Search](Examples/Product/SEARCH.md)   | Search all products             |
| /api/products/{id}   | products.view   | GET    | [View Product](Examples/Product/VIEW.md)       | Get product by id               | 
| /api/products        | products.store  | POST   | [Store Product](Examples/Product/STORE.md)     | Create a product from json data | 
| /api/products/{id}   | products.store  | PUT    | [Update Product](Examples/Product/UPDATE.md)   | Update a product from json data |

`/api/products` is paginated, see [Pagination Conventions](CONVENTIONS.md#pagination-conventions) for more info

`/api/products` supports image factory params, see [Image Factory Conventions](CONVENTIONS.md#image-factory-conventions) for more info

**NOTE:** The `/api/products/search` exists to allow filtering at elasticsearch document level rather than eloquent level

**NOTE:** The `view` and `update` product routes support passing the product's `model` instead of the `id`

### Variants

| URL                              | Permission      | Action | Examples                                     | Purpose                         |
|----------------------------------|-----------------|--------|----------------------------------------------|---------------------------------|
| /api/products/{id}/variants      | variants.store  | POST   | [Store Variant](Examples/Variant/STORE.md)   | Create a variant from json data |
| /api/products/{id}/variants/{id} | variants.update | PUT    | [Update Variant](Examples/Variant/UPDATE.md) | Update a variant from json data |

**NOTE:** The `update` variant route supports passing the variant's `sku` instead of the `id`

### Customers

| URL                   | Permission       | Action  | Examples                                       | Purpose                           |
|-----------------------|------------------|---------|------------------------------------------------|-----------------------------------|
| /api/customers        | customers.index  | GET     | [Customer Index](Examples/Customer/INDEX.md)   | Get all customers                 |
| /api/customers/{id}   | customers.view   | GET     | [View Customer](Examples/Customer/VIEW.md)     | Get customer by id                | 
| /api/customers        | customers.store  | POST    | [Store Customer](Examples/Customer/STORE.md)   | Create a customer from json data  | 
| /api/customers/{id}   | customers.update | PUT     | [Update Customer](Examples/Customer/UPDATE.md) | Update a customer from json data  |

`/api/customers` is paginated, see [Pagination Conventions](CONVENTIONS.md#pagination-conventions) for more info

### Addresses

| URL                                | Permission       | Action | Examples                                     | Purpose                          |
|------------------------------------|------------------|--------|----------------------------------------------|----------------------------------|
| /api/customers/{id}/addresses      | addresses.store  | POST   | [Store Address](Examples/Address/STORE.md)   | Create an address from json data | 
| /api/customers/{id}/addresses/{id} | addresses.update | PUT    | [Update Address](Examples/Address/UPDATE.md) | Update an address from json data |
| /api/customers/{id}/addresses/{id} | addresses.delete | DELETE | [Delete Address](Examples/Address/UPDATE.md) | Delete an address                |

### Payment Methods

| URL                        | Permission              | Action  | Examples                                                   | Purpose                    |
|----------------------------|-------------------------|---------|------------------------------------------------------------|----------------------------|
| /api/payment-methods       | payment-methods.index   | GET     | [Payment Method Index](Examples/PaymentMethod/INDEX.md)    | Get all payment methods    |
| /api/payment-methods/{id}  | payment-methods.view    | GET     | [View Payment Method](Examples/PaymentMethod/VIEW.md)      | Get payment method by id   | 

`/api/payment-methods` is paginated, see [Pagination Conventions](CONVENTIONS.md#pagination-conventions) for more info

### Flags

| URL              | Permission   | Action | Examples                                 | Purpose                      |
|------------------|--------------|--------|------------------------------------------|------------------------------|
| /api/flags       | flags.index  | GET    | [Flag Index](Examples/Flag/INDEX.md)     | Get all flags                |
| /api/flags/{id}  | flags.view   | GET    | [View Flag](Examples/Flag/VIEW.md)       | Get flags by id              | 
| /api/flags       | flags.store  | POST   | [Store Flag](Examples/Flag/STORE.md)     | Create a flag from json data | 
| /api/flags/{id}  | flags.update | PUT    | [Update Flag](Examples/Flag/UPDATE.md)   | Update a flag from json data |
| /api/flags/{id}  | flags.delete | DELETE | [Delete Flag](Examples/Flag/DELETE.md)   | Delete a flag                |

### Price Lists

| URL                   | Permission          | Action | Examples                                          | Purpose                            |
|-----------------------|---------------------|--------|---------------------------------------------------|------------------------------------|
| /api/price-lists      | price-lists.index   | GET    | [Price List Index](Examples/PriceList/INDEX.md)   | Get all price lists                |
| /api/price-lists/{id} | price-lists.view    | GET    | [View Price List](Examples/PriceList/VIEW.md)     | Get price list by id               | 
| /api/price-lists      | price-lists.store   | POST   | [Store Price List](Examples/PriceList/STORE.md)   | Create a price list from json data | 
| /api/price-lists/{id} | price-lists.store   | PUT    | [Update Price List](Examples/PriceList/UPDATE.md) | Update a price list from json data |

`/api/price-lists` is paginated, see [Pagination Conventions](CONVENTIONS.md#pagination-conventions) for more info

### Price List Entries

| URL                                  | Permission                | Action | Examples                                                     | Purpose                                  |
|--------------------------------------|---------------------------|--------|--------------------------------------------------------------|------------------------------------------|
| /api/price-lists/{id}/entries        | price-list-entries.store  | POST   | [Store Price List Entry](Examples/PriceListEntry/STORE.md)   | Create a price list entry from json data |
| /api/price-lists/{id}/entries/{id}   | price-list-entries.update | PUT    | [Update Price List Entry](Examples/PriceListEntry/UPDATE.md) | Update a price list entry from json data |


[Back to contents](README.md#table-of-contents)
