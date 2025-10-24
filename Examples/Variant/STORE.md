# Store Variant

## Overview

This endpoint creates a new variant for an existing **variant** product using the provided json data

## Structure

### Variant

| Name                    | Type    | Description                                                       | Required? |
|-------------------------|---------|-------------------------------------------------------------------|-----------|
| `id`                    | int     | The id for the variant                                            | No        |
| `sku`                   | string  | The **unique** SKU for the variant                                | Yes       |
| `reference`             | string  | The **unique** reference for the variant                          | No        |
| `name`                  | string  | Display name of the variant                                       | No        |
| `summary`               | string  | A short summary of the variant                                    | No        |
| `description`           | string  | A detailed description of the variant                             | No        |
| `barcode`               | string  | The barcode/UPC/EAN of the variant                                | No        |
| `buyable`               | boolean | Whether the variant can be purchased                              | No        |
| `visible`               | boolean | Whether the variant is visible in listings                        | No        |
| `shippable`             | boolean | Whether the variant is shippable                                  | No        |
| `discountable`          | boolean | Whether discounts can be applied to this variant                  | No        |
| `hide_when_no_stock`    | boolean | Whether the variant should be hidden when out of stock            | No        |
| `infinite_stock`        | boolean | Whether the variant has unlimited stock                           | No        |
| `stock_level`           | int     | Current stock level                                               | No        |
| `stock_buffer`          | int     | The stock buffer                                                  | No        |
| `tax_group`             | string  | The tax group applied to the variant                              | No        |
| `minimum_quantity`      | int     | Minimum quantity per purchase                                     | No        |
| `maximum_quantity`      | int     | Maximum quantity per purchase                                     | No        |
| `multiples_of`          | int     | Purchasable only in multiples of this number                      | No        |
| `weight`                | float   | Weight of the variant                                             | No        |
| `weight_unit`           | string  | Unit of weight (e.g., `kg`, `lb`)                                 | No        |
| `volume`                | float   | Volume of the variant                                             | No        |
| `volume_unit`           | string  | Unit of volume (e.g., `m^3`, `cm^3`)                              | No        |
| `hs`                    | string  | HS (Harmonized System) code for customs                           | No        |
| `origin_country`        | string  | ISO country code of origin (e.g., `US`, `GB`)                     | No        |
| `goods_description`     | string  | Description of goods for customs                                  | No        |
| `attributes`            | array   | An array of [Attribute](#attribute) objects                       | Yes       |
| `tags`                  | array   | An array of [Tag](#tag) objects                                   | No        |
| `images`                | array   | The images of the variant, see [Image](#image)                    | No        |
| `cost`                  | object  | The [Cost Price](#cost-price) of the variant                      | No        |
| `prices`                | array   | An array of [Price](#price) objects                               | Yes       |
| `additional_attributes` | array   | An array of [Additional Attribute](#additional-attribute) objects | No        |

### Attribute

| Name      | Type   | Description                                              | Required? |
|-----------|--------|----------------------------------------------------------|-----------|
| `name`    | string | The name of the attribute (e.g., "Small" or "Red")       | Yes       |
| `tags`    | array  | An array of [Tag](#tag) objects linked to the attribute  | No        |
| `group`   | object | The [Attribute Group](#attribute-group) of the attribute | Yes       |

### Attribute Group

| Name      | Type   | Description                                              | Required? |
|-----------|--------|----------------------------------------------------------|-----------|
| `name`    | string | The name of the attribute group (e.g., "Size", "Colour") | Yes       |

### Tag

| Name       | Type   | Description                                  | Required? |
|------------|--------|----------------------------------------------|-----------|
| `name`     | string | The name of the tag (e.g., "Small" or "Red") | Yes       |
| `group`    | object | The [Tag Group](#tag-group) of the tag       | Yes       |

### Tag Group

| Name      | Type   | Description                                          | Required? |
|-----------|--------|------------------------------------------------------|-----------|
| `name`    | string | The name of the tag group (e.g., "Size" or "Colour"  | Yes       |

### Image

| Name         | Type    | Description                                                          | Required? |
|--------------|---------|----------------------------------------------------------------------|-----------|
| `src`        | string  | The source url of the image                                          | Yes       |
| `alt`        | string  | Alt text for accessibility and SEO                                   | No        |
| `is_default` | boolean | Whether this is a default image                                      | No        |
| `position`   | int     | Sort order position of the image                                     | No        |
| `attributes` | array   | An array of [Attribute](#attribute) objects that apply to this image | No        |

### Cost Price

| Name       | Type   | Description                                                | Required? |
|------------|--------|------------------------------------------------------------|-----------|
| `amount`   | float  | The cost price **including tax**                           | Yes       |
| `currency` | string | Currency code (defaults to store default if not provided)  | No        |

### Price

| Name           | Type      | Description                                                | Required? |
|----------------|-----------|------------------------------------------------------------|-----------|
| `price`        | float     | The base price **including tax**                           | Yes       |
| `sale_price`   | float     | The sale price **including tax**                           | No        |
| `retail_price` | float     | The retail price **including tax**                         | No        |
| `quantity`     | int       | Quantity required for this price tier (default: 1)         | No        |
| `currency`     | string    | Currency code (defaults to store default)                  | No        |
| `start_at`     | timestamp | When this price becomes active (e.g., 2023-09-01 09:29:41) | No        |
| `end_at`       | timestamp | When this price expires                                    | No        |
| `reference`    | string    | The **unique** reference for the price                     | No        |

### Additional Attribute

| Name    | Type    | Description                           | Required? |
|---------|---------|---------------------------------------|-----------|
| `key`   | string  | The key of the additional attribute   | Yes       |
| `value` | string  | The value of the additional attribute | Yes       |

## Example Request

```http request
POST /api/products/{id|model}/variants
```

OR

```http request
POST /api/products/variants?model=model
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

[Back to contents](../../README.md#table-of-contents)
