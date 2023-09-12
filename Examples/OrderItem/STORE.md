# Store Order Item

## Attributes

| Name                   | Type    | Description                                                                                                  | Required? |
|------------------------|---------|--------------------------------------------------------------------------------------------------------------|-----------|
| `key`                  | string  | The key for the order item                                                                                   | No        |
| `variant_id`           | int     | The variant id of the buyable                                                                                | No        |
| `product_id`           | string  | The product id of the buyable (resolves first variant)                                                       | No        |
| `buyable_type`         | string  | The buyable type of the order item, not required if any of:<br/>`sku`/`variant_id`/`product_id` are provided | Yes (?)   |
| `buyable_id`           | int     | The buyable id of the order item, not required if any of:<br/>`sku`/`variant_id`/`product_id` are provided   | Yes (?)   |
| `name`                 | string  | The name for the order item                                                                                  | No        |
| `url`                  | string  | The url for the order item                                                                                   | No        |
| `sku`                  | string  | The sku for the order item, can be used to resolve buyable                                                   | No        |
| `reference`            | string  | The **unique** reference for the order item                                                                  | No        |
| `manufacturer_id`      | int     | The manufacturer id for the order item                                                                       | No        |
| `image`                | string  | The image for the order item                                                                                 | No        |
| `options`              | array   | The options for the order item                                                                               | No        |
| `shippable`            | boolean | Whether the order item is shippable                                                                          | No        |
| `quantity`             | int     | The quantity for the order item                                                                              | Yes       |
| `price.amount`         | float   | The **unit** price of the order item **excluding tax**                                                       | Yes       |
| `price.tax`            | float   | The **unit** tax for the order item                                                                          | Yes       |
| `discount.amount`      | float   | The **total** discount of the order item **excluding tax**                                                   | No        |
| `discount.tax`         | float   | The **total** discount tax for the order item                                                                | No        |
| `full_price.amount`    | float   | The **unit** full price (including extras) of the order item **excluding tax**                               | No        |
| `full_price.tax`       | float   | The **unit** full tax (including extras) for the order item                                                  | No        |
| `cost_price.amount`    | float   | The **unit** cost price of the order item **excluding tax**                                                  | No        |
| `cost_price.currency`  | string  | The currency code for the cost price                                                                         | No        |
| `weight`               | float   | The weight for the order item                                                                                | No        |
| `weight_unit`          | float   | The weight unit for the order item, defaults to stores normalized <br/> weight unit if not passed            | No        |
| `volume`               | float   | The volume for the order item                                                                                | No        |
| `volume_unit`          | float   | The volume unit for the order item, defaults to stores normalized <br/>volume unit if not passed             | No        |
| `tag_ids`              | array   | The tag ids for the order item                                                                               | No        |
| `hs`                   | string  | The HS code for the order item                                                                               | No        |
| `origin_country`       | string  | The origin country code for the order item                                                                   | No        |
| `subscription_plan_id` | int     | The subscription plan id for the order item                                                                  | No        |
| `goods_description`    | string  | The goods description for the order item                                                                     | No        |

## Remarks

The majority of the fields above are resolved from the item's buyable if not specified

The item's buyable is resolved using the following priority:
1. Looks for `"buyable_type"` & `"buyable_id"`
2. If not present, looks for `"sku"`
3. If not present, looks for `"variant_id"`
4. If not present, looks for `"product_id"`
5. If not present validation will fail

If `full_price` is not specified then `price` will be used for its value

[Back to contents](../../README.md#table-of-contents)
