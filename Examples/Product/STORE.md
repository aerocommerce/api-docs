# Store Product

## Overview

This endpoint creates a new product using the provided json data

## Structure

### Product

| Name                           | Type        | Description                                                            | Required?            |
|--------------------------------|-------------|------------------------------------------------------------------------|----------------------|
| `id`                           | int         | The id for the product                                                 | No                   |
| `model`                        | string      | The **unique** model identifier for the product                        | Yes                  |
| `name`                         | string      | The display name of the product                                        | Yes                  |
| `manufacturer`                 | string      | The manufacturer/brand of the product                                  | No                   |
| `summary`                      | string      | A short summary of the product                                         | No                   |
| `description`                  | string      | A detailed description of the product                                  | No                   |
| `active`                       | boolean     | Whether the product is active (available for purchase)                 | No                   |
| `visible`                      | boolean     | Whether the product is visible in the storefront                       | No                   |
| `attribute_groups_to_split_by` | array       | An array of attribute group names to split listings by (e.g., ["Size"] | No                   |
| `published_at`                 | timestamp   | When the product was published                                         | No                   |
| `images`                       | array       | An array of [Image](#image) objects                                    | No                   |
| `categories`                   | array       | An array of [Category](#category) objects                              | No                   |
| `tags`                         | array       | An array of [Tag](#tag) objects                                        | No                   |
| `variants`                     | array       | An array of [Variant](#variant) objects                                | Yes                  |
| `seo`                          | object      | A [SEO](#seo) object                                                   | No                   |
| `settings`                     | object      | A [Settings](#settings) object with grouped key-value pairs            | No                   |
| `additional_attributes`        | array       | An array of [Additional Attribute](#additional-attribute) objects      | No                   |
| `specifications`               | array       | An array of [Specification](#specification) objects                    | No                   |
| `upsells`                      | array       | An array of [Upsell](#upsell) objects                                  | No                   |
| `related_listings`             | array       | An array of [Related Listing](#related-listing) objects                | No                   |

### Category

| Name                    | Type      | Description                                                         | Required? |
|-------------------------|-----------|---------------------------------------------------------------------|-----------|
| `name`                  | string    | The category name or breadcrumb (e.g., "Coats" or "Mens > "Coats")  | Yes       |

### Variant

| Name                     | Type     | Description                                                       | Required?                        |
|--------------------------|----------|-------------------------------------------------------------------|----------------------------------|
| `id`                     | int      | The id for the variant                                            | No                               |
| `sku`                    | string   | The **unique** SKU for the variant                                | Yes                              |
| `reference`              | string   | The **unique** reference for the variant                          | No                               |
| `name`                   | string   | Display name of the variant                                       | No                               |
| `summary`                | string   | A short summary of the variant                                    | No                               |
| `description`            | string   | A detailed description of the variant                             | No                               |
| `barcode`                | string   | The barcode/UPC/EAN of the variant                                | No                               |
| `buyable`                | boolean  | Whether the variant can be purchased                              | No                               |
| `visible`                | boolean  | Whether the variant is visible in listings                        | No                               |
| `shippable`              | boolean  | Whether the variant is shippable                                  | No                               |
| `discountable`           | boolean  | Whether discounts can be applied to this variant                  | No                               |
| `hide_when_no_stock`     | boolean  | Whether the variant should be hidden when out of stock            | No                               |
| `infinite_stock`         | boolean  | Whether the variant has unlimited stock                           | No                               |
| `stock_level`            | int      | Current stock level                                               | No                               |
| `stock_buffer`           | int      | The stock buffer                                                  | No                               |
| `tax_group`              | string   | The tax group applied to the variant                              | No                               |
| `minimum_quantity`       | int      | Minimum quantity per purchase                                     | No                               |
| `maximum_quantity`       | int      | Maximum quantity per purchase                                     | No                               |
| `multiples_of`           | int      | Purchasable only in multiples of this number                      | No                               |
| `weight`                 | float    | Weight of the variant                                             | No                               |
| `weight_unit`            | string   | Unit of weight (e.g., `kg`, `lb`)                                 | No                               |
| `volume`                 | float    | Volume of the variant                                             | No                               |
| `volume_unit`            | string   | Unit of volume (e.g., `m^3`, `cm^3`)                              | No                               |
| `hs`                     | string   | HS (Harmonized System) code for customs                           | No                               |
| `origin_country`         | string   | ISO country code of origin (e.g., `US`, `GB`)                     | No                               |
| `goods_description`      | string   | Description of goods for customs                                  | No                               |
| `attributes`             | array    | An array of [Attribute](#attribute) objects                       | Required if product has variants |
| `tags`                   | array    | An array of [Tag](#tag) objects                                   | No                               |
| `cost`                   | object   | The [Cost Price](#cost-price) of the variant                      | No                               |
| `prices`                 | array    | An array of [Price](#price) objects                               | Yes                              |
| `additional_attributes`  | array    | An array of [Additional Attribute](#additional-attribute) objects | No                               |
| `specifications`         | array    | An array of [Specification](#specification) objects               | No                               |
| `upsells`                | array    | An array of [Upsell](#upsell) objects                             | No                               |

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

### SEO

| Name               | Type      | Description                | Required? |
|--------------------|-----------|----------------------------|-----------|
| `heading`          | string    | The SEO Heading            | No        |
| `page_title`       | string    | The SEO Page Title         | No        |
| `meta_description` | string    | The SEO Meta Description   | No        |
| `canonical`        | string    | The SEO Canonical          | No        |
| `noindex`          | boolean   | The SEO No Index           | No        |
| `nofollow`         | boolean   | The SEO No Follow          | No        |

### Settings

Settings are grouped as key-value pairs.
- Use "_" for ungrouped settings.
- Each group contains its own object of key-value pairs.

```json
{
    "settings": {
        "_": {
            "no_group": "value"
        },
        "group": {
            "key": "value"
        }
    }
}
```

### Additional Attribute

| Name    | Type    | Description                           | Required? |
|---------|---------|---------------------------------------|-----------|
| `key`   | string  | The key of the additional attribute   | Yes       |
| `value` | string  | The value of the additional attribute | Yes       |

### Specification

| Name         | Type   | Description                         | Required? |
|--------------|--------|-------------------------------------|-----------|
| `group.name` | string | The name of the specification group | Yes       |
| `name`       | string | The name of the specification       | Yes       |
| `value`      | string | The value of the specification      | Yes       |

### Upsell

| Name         | Type   | Description                                                           | Required? |
|--------------|--------|-----------------------------------------------------------------------|-----------|
| `group.key`  | string | The upsell group key                                                  | Yes       |
| `attributes` | array  | An array of [Attribute](#attribute) objects that the upsell shows for | No        |
| `models`     | array  | And array of models for the upsell                                    | No        |
| `skus`       | array  | And array of SKUs for the upsell                                      | No        |

### Related Listing

| Name         | Type   | Description                               | Required?          |
|--------------|--------|-------------------------------------------|--------------------|
| `id`         | int    | The id of the listing                     | Conditional `*`    |
| `variant_id` | int    | The id of the variant (of the listing)    | Conditional `*`    |
| `sku`        | string | The SKU of the variant (of the listing)   | Conditional `*`    |
| `product_id` | int    | The id of the product (of the listing)    | Conditional `*`    |
| `model`      | string | The model of the product (of the listing) | Conditional `*`    |

`*` At least one must be present, resolved in the order they are listed top-down

## Example Request

```http request
POST /api/products
```

### Simple Product (One variant without any attributes)

```json lines
{
    "model": "9021182",
    "name": "Detachable Sleeve Puffer Jacket",
    "manufacturer": "Burberry",
    "categories": [
        { 
            "name": "Mens > Coats > Padded Coats"
        }
    ],
    "summary": "Summary",
    "description": "Description",
    "active": true,
    "visible": true,
    "images": [
        {
            "src": "https://picsum.photos/seed/first/600/400",
            "is_default": true
        }
    ],
    "variants": [
        {
            "sku": "9021182",
            "barcode": "abc123",
            "stock_level": 5,
            "prices": [
                {
                    "currency": "GBP",
                    "price": 790,
                    "quantity": 1
                }
            ],
            "tax_group": "Taxable Product"
        }
    ],
    "tags": [
        {
            "group": { 
                "name": "Colour"
            },
            "name": "Blue"
        }
    ],
    "seo": {
        "heading": "test heading",
        "page_title": "test page title",
        "meta_description": "test meta description",
        "noindex": 0,
        "nofollow": 0
    },
    "additional_attributes": [
        {
            "key": "test_name",
            "value": "test_value"
        }
    ]
}
```

### Variant Product (Multiple variants with shared attribute matrix structure)

```json lines
{
    "model": "9021182",
    "name": "Detachable Sleeve Puffer Jacket",
    "manufacturer": "Burberry",
    "categories": [
        {
            "name": "Mens > Coats > Padded Coats"
        }
    ],
    "summary": "Outer: Leather 100%, Polyamide 100%\nLining: Polyester 100%, Goose Down 90%, Wool 70%, Polyamide 20%, Cashmere 10%, Feather 10%",
    "description": "A quintessentially British brand, Burberry creates iconic designs that seamlessly infuse their rich heritage with a contemporary aesthetic. This deep blue wool and cashmere blend detachable sleeve puffer jacket from Burberry features a hood, a high standing collar, a zip and press stud fastening, detachable long sleeves, a contrast logo patch to one side, zipped side slit pockets and a puffer style.",
    "images": [
        {
            "src": "https://picsum.photos/seed/first/600/400",
            "is_default": "1"
        },
        {
            "src": "https://picsum.photos/seed/second/600/400",
            "is_default": "1"
        },
        {
            "src": "https://picsum.photos/seed/third/600/400",
            "is_default": "1"
        },
        {
            "src": "https://picsum.photos/seed/fourth/600/400",
            "is_default": "1",
            "attributes": [
                {
                    "group": {
                        "name": "Size"
                    },
                    "name": "Small"
                }
            ]
        }
    ],
    "variants": [
        {
            "sku": "9021182-S",
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
                    "name": "Small",
                    "tags": [
                        {
                            "group": {
                                "name": "Size"
                            },
                            "name": "Small"
                        }
                    ]
                }
            ],
            "stock_buffer": 0,
            "minimum_quantity": 1,
            "multiples_of": 1
        },
        {
            "sku": "9021182-M",
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
                    "name": "Medium",
                    "tags": [
                        {
                            "group": {
                                "name": "Size"
                            },
                            "name": "Medium"
                        }
                    ]
                }
            ],
            "stock_buffer": 0,
            "minimum_quantity": 1,
            "multiples_of": 1
        },
        {
            "sku": "9021182-L",
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
                    "name": "Large",
                    "tags": [
                        {
                            "group": {
                                "name": "Size"
                            },
                            "name": "Large"
                        }
                    ]
                }
            ],
            "stock_buffer": 0,
            "minimum_quantity": 1,
            "multiples_of": 1
        },
        {
            "sku": "9021182-XL",
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
                    "name": "Extra Large",
                    "tags": [
                        {
                            "group": {
                                "name": "Size"
                            },
                            "name": "Extra Large"
                        }
                    ]
                }
            ],
            "stock_buffer": 0,
            "minimum_quantity": 1,
            "multiples_of": 1
        }
    ],
    "tags": [
        {
            "group": {
                "name": "Colour"
            },
            "name": "Blue"
        }
    ],
    "active": true,
    "visible": true,
    "hide_when_no_stock": false,
    "seo": {
        "heading": "test heading",
        "page_title": "test page title",
        "meta_description": "test meta description",
        "noindex": 0,
        "nofollow": 0
    },
    "settings": {
        "_": {
            "no_group": "value"
        },
        "group": {
            "key": "value"
        }
    },
    "additional_attributes": [
        {
            "key": "test_name",
            "value": "test_value"
        }
    ]
}
```

## Example Response

```json
{
    "product": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
