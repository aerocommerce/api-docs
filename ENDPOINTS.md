## Endpoints

### Orders

| URL               | Permission   | Action | Payload                                  | Purpose                        |
|-------------------|--------------|--------|------------------------------------------|--------------------------------|
| /api/orders/{id}  | orders.view  | GET    | N/A                                      | Get an order by id             |
| /api/orders       | orders.store | POST   | [Store Order](Payloads/Order/STORE.md)   | Create an order from json data |

[Back to contents](README.md#table-of-contents)
