# View Order Item

## Attributes

| Name                  | Type    | Description                                                                                       |
|-----------------------|---------|---------------------------------------------------------------------------------------------------|
| `id`                  | int     | The id of the order item                                                                          |
| `variant_id`          | int     | The variant id of the buyable (not set if the buyable is not a variant)                           |
| `product_id`          | int     | The product id of the buyable                                                                     |
| `buyable_type`        | string  | The buyable type of the order item                                                                |
| `buyable_id`          | int     | The buyable id of the order item                                                                  |
| `name`                | string  | The name for the order item                                                                       |
| `url`                 | string  | The url for the order item                                                                        |
| `sku`                 | string  | The sku for the order item                                                                        |
| `reference`           | string  | The **unique** reference for the order item                                                       |
| `manufacturer`        | object  | The manufacturer for the order item, see [View Manufacturer](../Manufacturer/VIEW.md)             |
| `image.url`           | string  | The image url for the order item                                                                  |
| `shippable`           | boolean | Whether the order item is shippable                                                               |
| `quantity`            | int     | The quantity for the order item                                                                   |
| `price.amount`        | float   | The **unit** price of the order item **excluding tax**                                            |
| `price.tax`           | float   | The **unit** tax for the order item                                                               |
| `discount.amount`     | float   | The **total** discount of the order item **excluding tax**                                        |
| `discount.tax`        | float   | The **total** discount tax for the order item                                                     |
| `full_price.amount`   | float   | The **unit** full price (including extras) of the order item **excluding tax**                    |
| `full_price.tax`      | float   | The **unit** full tax (including extras) for the order item                                       |
| `cost_price.amount`   | float   | The **unit** cost price of the order item **excluding tax**                                       |
| `cost_price.currency` | string  | The currency code for the cost price                                                              |
| `weight`              | float   | The weight for the order item                                                                     |
| `weight_unit`         | float   | The weight unit for the order item, defaults to stores normalized <br/> weight unit if not passed |
| `volume`              | float   | The volume for the order item                                                                     |
| `volume_unit`         | float   | The volume unit for the order item, defaults to stores normalized <br/>volume unit if not passed  |
| `hs`                  | string  | The HS code for the order item                                                                    |
| `origin_country`      | string  | The origin country code for the order item                                                        |
| `goods_description`   | string  | The goods description for the order item                                                          |

[Back to contents](../../README.md#table-of-contents)
