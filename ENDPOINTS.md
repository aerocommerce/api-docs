## Endpoints

### Orders

| URL               | Permission   | Action | Examples                               | Purpose                        |
|-------------------|--------------|--------|----------------------------------------|--------------------------------|
| /api/orders/{id}  | orders.view  | GET    | [View Order](Examples/Order/VIEW.md)   | Get an order by id             |
| /api/orders       | orders.store | POST   | [Store Order](Examples/Order/STORE.md) | Create an order from json data |

### Products

| URL                | Permission     | Action | Examples                                   | Purpose           |
|--------------------|----------------|--------|--------------------------------------------|-------------------|
| /api/products      | products.index | GET    | [Product Index](Examples/Product/INDEX.md) | Get all products  |
| /api/products/{id} | products.view  | GET    | [View Product](Examples/Product/VIEW.md)   | Get product by id | 

`/api/products` is paginated, see [Pagination Conventions](CONVENTIONS.md#pagination-conventions) for more info

[Back to contents](README.md#table-of-contents)
