## Endpoints

### Orders

| URL               | Permission   | Action | Examples                               | Purpose                        |
|-------------------|--------------|--------|----------------------------------------|--------------------------------|
| /api/orders/{id}  | orders.view  | GET    | [View Order](Examples/Order/VIEW.md)   | Get an order by id             |
| /api/orders       | orders.store | POST   | [Store Order](Examples/Order/STORE.md) | Create an order from json data |

### Order Statuses

| URL                      | Permission            | Action | Examples                                             | Purpose                |
|--------------------------|-----------------------|--------|------------------------------------------------------|------------------------|
| /api/order-statuses      | order-statuses.index  | GET    | [Order Status Index](Examples/OrderStatus/INDEX.md)  | Get all order statuses |
| /api/order-statuses/{id} | order-statuses.view   | GET    | [View Order Status](Examples/OrderStatus/VIEW.md)    | Get order status by id | 

`/api/order-statuses` is paginated, see [Pagination Conventions](CONVENTIONS.md#pagination-conventions) for more info

### Products

| URL                | Permission      | Action | Examples                                     | Purpose                         |
|--------------------|-----------------|--------|----------------------------------------------|---------------------------------|
| /api/products      | products.index  | GET    | [Product Index](Examples/Product/INDEX.md)   | Get all products                |
| /api/products/{id} | products.view   | GET    | [View Product](Examples/Product/VIEW.md)     | Get product by id               | 
| /api/products      | products.store  | POST   | [Store Product](Examples/Product/STORE.md)   | Create a product from json data | 
| /api/products/{id} | products.update | PUT    | [Update Product](Examples/Product/UPDATE.md) | Update a product from json data |

`/api/products` is paginated, see [Pagination Conventions](CONVENTIONS.md#pagination-conventions) for more info

`/api/products` supports image factory params, see [Image Factory Conventions](CONVENTIONS.md#image-factory-conventions) for more info

**NOTE:** The `view` and `update` product routes support passing the product's `model` instead of the `id`

### Variants

| URL                              | Permission      | Action | Examples                                        | Purpose                         |
|----------------------------------|-----------------|--------|-------------------------------------------------|---------------------------------|
| /api/products/{id}/variants      | products.store  | POST   | [Store Variant](Examples/Variant/STORE.md)      | Create a variant from json data |
| /api/products/{id}/variants/{id} | products.update | PUT    | [Update Product](Examples/Product/UPDATE.md)    | Update a variant from json data |

### Payment Methods

| URL                        | Permission              | Action  | Examples                                                   | Purpose                    |
|----------------------------|-------------------------|---------|------------------------------------------------------------|----------------------------|
| /api/payment-methods       | payment-methods.index   | GET     | [Payment Method Index](Examples/PaymentMethod/INDEX.md)    | Get all payment methods    |
| /api/payment-methods/{id}  | payment-methods.view    | GET     | [View Payment Method](Examples/PaymentMethod/VIEW.md)      | Get payment method by id   | 

`/api/payment-methods` is paginated, see [Pagination Conventions](CONVENTIONS.md#pagination-conventions) for more info

[Back to contents](README.md#table-of-contents)
