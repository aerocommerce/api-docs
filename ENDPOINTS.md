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

| URL                | Permission     | Action | Examples                                   | Purpose           |
|--------------------|----------------|--------|--------------------------------------------|-------------------|
| /api/products      | products.index | GET    | [Product Index](Examples/Product/INDEX.md) | Get all products  |
| /api/products/{id} | products.view  | GET    | [View Product](Examples/Product/VIEW.md)   | Get product by id | 

`/api/products` is paginated, see [Pagination Conventions](CONVENTIONS.md#pagination-conventions) for more info

The following query parameters can be passed in order to use Image Factory for generating the product's images urls

| Parameter               | Description             | Example                               |
|-------------------------|-------------------------|---------------------------------------|
| `image_factory_width`   | The width               | ?image_factory_width=200              |
| `image_factory_height`  | The height              | ?image_factory_height=200             |
| `image_factory_options` | Comma seperated options | ?image_factory_options=flip,greyscale |

If any of these query parameters are present in the GET requests then the Image Factory will be used

[Back to contents](README.md#table-of-contents)
