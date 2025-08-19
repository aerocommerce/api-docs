# Store Variant

## Attributes:

### Variant
| Name                    | Type     | Description                                                                                 | Required? |
|-------------------------|----------|---------------------------------------------------------------------------------------------|-----------|
| `sku`                   | string   | The **unique** SKU for the variant                                                          | Yes       |
| `reference`             | string   | The **unique** reference for the variant                                                    | No        |
| `name`                  | string   | The name of the variant                                                                     | No        |
| `summary`               | string   | The summary of the variant                                                                  | No        |
| `description`           | string   | The description of the variant                                                              | No        |
| `barcode`               | string   | The barcode of the variant                                                                  | No        |
| `buyable`               | boolean  | Whether the variant is buyable                                                              | No        |
| `visible`               | boolean  | Whether the variant is visible                                                              | No        |
| `shippable`             | boolean  | Whether the variant is shippable                                                            | No        |
| `discountable`          | boolean  | Whether the variant is discountable                                                         | No        |
| `hide_when_no_stock`    | boolean  | Whether the variant gets hidden when it has no stock                                        | No        |
| `infinite_stock`        | boolean  | Whether the variant has infinite stock                                                      | No        |
| `stock_level`           | int      | The stock level of the variant                                                              | No        |
| `stock_buffer`          | int      | The stock buffer of the variant                                                             | No        |
| `tax_group`             | string   | The tax group of the variant                                                                | No        |
| `minimum_quantity`      | int      | The minimum quantity of the variant that can be bought                                      | No        |
| `maximum_quantity`      | int      | The maximum quantity of the variant that can be bought                                      | No        |
| `multiples_of`          | int      | Only able to purchase in multiples of this number                                           | No        |
| `weight`                | float    | The weight of the variant                                                                   | No        |
| `weight_unit`           | string   | The weight unit of the variant                                                              | No        |
| `volume`                | float    | The volume of the variant                                                                   | No        |
| `volume_unit`           | string   | The volume unit of the variant                                                              | No        |
| `hs`                    | string   | The hs code of the variant                                                                  | No        |
| `origin_country`        | string   | The origin country code of the variant                                                      | No        |
| `goods_description`     | string   | The description of goods of the variant                                                     | No        |
| `attributes`            | array    | The attributes of the variant, see [Attribute](#attribute)                                  | Yes       |
| `tags`                  | array    | The tags of the variant, see [Tag](#tag)                                                    | No        |
| `images`                | array    | The images of the variant, see [Image](#image)                                              | No        |
| `cost`                  | object   | The cost price of the variant, see [Cost Price](#cost-price)                                | No        |
| `prices`                | array    | The prices of the variant, see [Price](#price)                                              | Yes       |
| `additional_attributes` | array    | The additional attributes of the variant, see [Additional Attribute](#additional-attribute) | No        |

### Attribute

| Name      | Type   | Description                                                  | Required? |
|-----------|--------|--------------------------------------------------------------|-----------|
| `name`    | string | The name of the attribute                                    | Yes       |
| `tags`    | array  | The tags linked to the attribute, see [Tag](#tag)            | No        |
| `group`   | object | The attribute group, see [Attribute Group](#attribute-group) | Yes       |

### Attribute Group

| Name      | Type   | Description                     | Required? |
|-----------|--------|---------------------------------|-----------|
| `name`    | string | The name of the attribute group | Yes       |

### Tag

| Name       | Type   | Description                                | Required? |
|------------|--------|--------------------------------------------|-----------|
| `name`     | string | The name of the tag                        | Yes       |
| `group`    | object | The tag group, see [Tag Group](#tag-group) | Yes       |

### Tag Group

| Name      | Type   | Description               | Required? |
|-----------|--------|---------------------------|-----------|
| `name`    | string | The name of the tag group | Yes       |

### Image

| Name         | Type    | Description                                                                | Required? |
|--------------|---------|----------------------------------------------------------------------------|-----------|
| `src`        | string  | The src of the image                                                       | Yes       |
| `alt`        | string  | The alt of the image                                                       | No        |
| `is_default` | boolean | Whether the image is default                                               | No        |
| `position`   | integer | The position/sort of the image                                             | No        |
| `attributes` | array   | The attributes that the image should show for, see [Attribute](#attribute) | Yes       |

### Image

| Name         | Type    | Description                                                                | Required? |
|--------------|---------|----------------------------------------------------------------------------|-----------|
| `src`        | string  | The src of the image                                                       | Yes       |
| `alt`        | string  | The alt of the image                                                       | No        |
| `is_default` | boolean | Whether the image is default                                               | No        |
| `position`   | integer | The position/sort of the image                                             | No        |
| `attributes` | array   | The attributes that the image should show for, see [Attribute](#attribute) | No        |

### Cost Price

| Name       | Type  | Description                                                     | Required? |
|------------|-------|-----------------------------------------------------------------|-----------|
| `amount`   | float | The cost price including tax                                    | Yes       |
| `currency` | float | The currency of the cost price (uses store default as fallback) | No        |

### Price

| Name           | Type      | Description                                                                  | Required? |
|----------------|-----------|------------------------------------------------------------------------------|-----------|
| `price`        | float     | The price including tax                                                      | Yes       |
| `sale_price`   | float     | The sale price including tax                                                 | No        |
| `retail_price` | float     | The retail price including tax                                               | No        |
| `quantity`     | integer   | The quantity needed to be purchased for this price to apply, defaults to `1` | No        |
| `currency`     | float     | The currency of the cost price (uses store default as fallback)              | No        |
| `start_at`     | timestamp | The date & time this price is available from                                 | No        |
| `end_at`       | timestamp | The date & time this price is available to                                   | No        |
| `reference`    | string    | The **unique** reference for the price                                       | No        |

### Additional Attribute

| Name    | Type    | Description                           | Required? |
|---------|---------|---------------------------------------|-----------|
| `key`   | string  | The key of the additional attribute   | Yes       |
| `value` | string  | The value of the additional attribute | Yes       |

## Example Request

```http request
POST /api/products/{productId}/variants
```

```json lines
{
    "sku": "9021182-XS",
    "stock_level": "5",
    "prices": [
        {
            "currency": "GBP",
            "price": "790",
            "quantity": 1
        }
    ],
    "tax_group": "Taxable Product",
    "attributes": [
        {
            "group": {
                "name": "Size"
            },
            "name": "Extra Small",
            "tags": [
                {
                    "group": {
                        "name": "Size"
                    },
                    "name": "Extra Small"
                }
            ]
        }
    ],
    "stock_buffer": 0,
    "minimum_quantity": 1,
    "multiples_of": 1
}
```

## Example Response

```json
{
    "variant": {
        "id": 1
    }
}
```
