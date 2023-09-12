# View Product

## Attributes

| Name                | Type    | Description                                                               |
|---------------------|---------|---------------------------------------------------------------------------|
| `id`                | int     | The id of the variant                                                     |
| `sku`               | string  | The sku of the variant                                                    |
| `reference`         | string  | The reference of the variant                                              |
| `name`              | string  | The name of the variant                                                   |
| `summary`           | string  | The summary of the variant                                                |
| `description`       | string  | The description of the variant                                            |
| `barcode`           | string  | The barcode of the variant                                                |
| `infinite_stock`    | boolean | Whether the variant has infinite stock                                    |
| `stock_level`       | int     | The stock level of the variant                                            |
| `stock_buffer`      | int     | The stock buffer of the variant                                           |
| `weight`            | float   | The weight of the variant                                                 |
| `weight_unit`       | string  | The unit for the weight                                                   |
| `volume`            | float   | The volume of the variant                                                 |
| `volume_unit`       | string  | The unit for the volume                                                   |
| `hs`                | string  | The hs code for the variant                                               |
| `origin_country`    | string  | The origin country code for the variant                                   |
| `goods_description` | string  | The goods description for the variant                                     |
| `cost.amount`       | float   | The cost price of the variant (excluding tax)                             |
| `cost.currency`     | string  | The currency for the cost price                                           |
| `price.amount`      | float   | The current price of the variant (excluding tax)                          |
| `price.tax`         | float   | The tax of the current price                                              |
| `price.currency`    | string  | The currency of the current price                                         |
| `retail.amount`     | float   | The RRP for the variant (excluding tax)                                   |
| `retail.tax`        | float   | The tax of the RRP                                                        |
| `retail.currency`   | string  | The currency of the RRP                                                   |
| `prices`            | array   | The prices of the variant, see [View Price](../Price/VIEW.md)             |
| `images`            | array   | The images of the variant, see [View Image](../Image/VIEW.md)             |
| `attributes`        | array   | The attributes of the variant, see [View Attribute](../Attribute/VIEW.md) |


