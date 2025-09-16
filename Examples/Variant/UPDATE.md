# Update Variant

## Overview

This endpoint updates an existing variant by its `id` or `sku`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Variant

| Name                    | Type     | Description                                                       | Required? |
|-------------------------|----------|-------------------------------------------------------------------|-----------|
| `sku`                   | string   | The **unique** SKU for the variant to be updated                  | Yes       |
| `reference`             | string   | The **unique** reference for the variant                          | No        |
| `name`                  | string   | Display name of the variant                                       | No        |
| `summary`               | string   | A short summary of the variant                                    | No        |
| `description`           | string   | A detailed description of the variant                             | No        |
| `barcode`               | string   | The barcode/UPC/EAN of the variant                                | No        |
| `buyable`               | boolean  | Whether the variant can be purchased                              | No        |
| `visible`               | boolean  | Whether the variant is visible in listings                        | No        |
| `shippable`             | boolean  | Whether the variant is shippable                                  | No        |
| `discountable`          | boolean  | Whether discounts can be applied to this variant                  | No        |
| `hide_when_no_stock`    | boolean  | Whether the variant should be hidden when out of stock            | No        |
| `infinite_stock`        | boolean  | Whether the variant has unlimited stock                           | No        |
| `stock_level`           | int      | Current stock level                                               | No        |
| `stock_buffer`          | int      | The stock buffer                                                  | No        |
| `tax_group`             | string   | The tax group applied to the variant                              | No        |
| `minimum_quantity`      | int      | Minimum quantity per purchase                                     | No        |
| `maximum_quantity`      | int      | Maximum quantity per purchase                                     | No        |
| `multiples_of`          | int      | Purchasable only in multiples of this number                      | No        |
| `weight`                | float    | Weight of the variant                                             | No        |
| `weight_unit`           | string   | Unit of weight (e.g., `kg`, `lb`)                                 | No        |
| `volume`                | float    | Volume of the variant                                             | No        |
| `volume_unit`           | string   | Unit of volume (e.g., `m^3`, `cm^3`)                              | No        |
| `hs`                    | string   | HS (Harmonized System) code for customs                           | No        |
| `origin_country`        | string   | ISO country code of origin (e.g., `US`, `GB`)                     | No        |
| `goods_description`     | string   | Description of goods for customs                                  | No        |
| `images`                | array    | An array of [Image](#image) objects                               | No        |
| `tags`                  | array    | An array of [Tag](#tag) objects                                   | No        |
| `cost`                  | object   | The [Cost Price](#cost-price) of the variant                      | No        |
| `prices`                | array    | An array of [Price](#price) objects                               | No        |
| `additional_attributes` | array    | An array of [Additional Attribute](#additional-attribute) objects | No        |

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
| `position`   | integer | Sort order position of the image                                     | No        |
| `attributes` | array   | An array of [Attribute](#attribute) objects that apply to this image | No        |

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
| `quantity`     | integer   | Quantity required for this price tier (default: 1)         | No        |
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

### 1. Update Basic Variant Details

```http request
PUT /api/products/{id|model}/variants/{id|sku}
```

```json lines
{
    "stock_level": 50,
    "buyable": true,
    "prices": [
        {
            "price": 199.99,
            "sale_price": 179.99,
            "currency": "GBP"
        }
    ],
    "cost": {
        "amount": 350,
        "currency": "GBP"
    }
}
```

### 2. Add Tags To Variant

```http request
PUT /api/products/{id|model}/variants/{id|sku}
```

```json lines
{
    "tags": [
        {
            "group": { 
                "name": "Size"
            },
            "name": "Small"
        },
        {
            "group": { 
                "name": "Style"
            },
            "name": "Casual"
        }
    ]
}
```

### 3. Add Images To Variant

```http request
PUT /api/products/{id|model}/variants/{id|sku}
```

```json lines
{
    "images": [
        {
            "src": "https://picsum.photos/seed/puffer-s/600/400",
            "alt": "Small size jacket, front view",
            "is_default": true,
            "position": 1,
            "attributes": [
                {
                    "name": "Small",
                    "group": {
                        "name": "Size"
                    }
                }
            ]
        }
    ]
}
```

**NOTE:** Variant images must include at least one attribute, and each attribute must exactly match one of the variant’s attributes

### 4. Add Additional Attributes To Variant

```http request
PUT /api/products/{id|model}/variants/{id|sku}
```

```json lines
{
    "additional_attributes": [
        { 
            "key": "material", 
            "value": "100% leather"
        },
        { 
            "key": "lining", 
            "value": "Polyester"
        }
    ]
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
