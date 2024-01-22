# View Shipping Method

## Attributes:

### Shipping Method

| Name        | Type    | Description                                            |
|-------------|---------|--------------------------------------------------------|
| `id`        | int     | The id of the shipping method                          |
| `name`      | string  | The name of the shipping method                        |
| `available` | boolean | Whether the shipping method is available for use       |
| `rates`     | array   | The rates for the shipping method, see [Rates](#rates) |

### Rates

| Name         | Type   | Description                                                                         |
|--------------|--------|-------------------------------------------------------------------------------------|
| `id`         | int    | The id of the shipping rate                                                         |
| `currency`   | string | The currency code of the shipping rate                                              |
| `min_price`  | int    | The minimum total price of the cart items for this shipping method to be applicable |
| `max_price`  | int    | The maximum total price of the cart items for this shipping method to be applicable |
| `min_weight` | int    | The minimum weight of the cart items for this shipping method to be applicable      |
| `max_weight` | int    | The maximum weight of the cart items for this shipping method to be applicable      |
| `min_volume` | int    | The minimum volume of the cart items for this shipping method to be applicable      |
| `max_volume` | int    | The maximum volume of the cart items for this shipping method to be applicable      |
| `rates`      | array  | The rates for the shipping method                                                   |


## Example Response

```http request
GET /api/shipping-methods/{id}
```

```json lines
{
    "id": 2,
    "name": "123",
    "available": true,
    "rates": [
        {
            "id": 2,
            "currency": "GBP",
            "min_price": 1000,
            "max_price": null,
            "min_weight": 0,
            "max_weight": null,
            "min_volume": 0,
            "max_volume": null,
            "price": 12300
        }
    ]
}
```
