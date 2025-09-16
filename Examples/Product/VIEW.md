# View Product

## Overview

This endpoint retrieves a single product by `id` or `model`

## Structure

### Product

| Name                            | Type      | Description                                                       |
|---------------------------------|-----------|-------------------------------------------------------------------|
| `model`                         | string    | The **unique** model identifier for the product                   |
| `name`                          | string    | The display name of the product                                   |
| `manufacturer`                  | object    | The [Manufacturer](#manufacturer) object (null when none)         |
| `summary`                       | string    | A short summary of the product                                    |
| `description`                   | string    | A detailed description of the product                             |
| `active`                        | boolean   | Whether the product is active (available for purchase)            |
| `visible`                       | boolean   | Whether the product is visible in the storefront                  |
| `attribute_groups_to_split_by`  | ?array    | The attribute groups to split listings by (null when none)        |
| `published_at`                  | timestamp | When the product was published                                    |
| `images`                        | array     | An array of [Image](#image) objects                               |
| `categories`                    | array     | An array of [Category](#category) objects                         |
| `tags`                          | array     | An array of [Tag](#tag) objects                                   |
| `variants`                      | array     | An array of [Variant](#variant) objects                           |
| `seo`                           | object    | A [SEO](#seo) object                                              |
| `settings`                      | object    | A [Settings](#settings) object with grouped key-value pairs       |
| `additional_attributes`         | array     | An array of [Additional Attribute](#additional-attribute) objects |

### Manufacturer

| Name    | Type   | Description                  |
|---------|--------|------------------------------|
| `id`    | int    | The id of the manufacturer   |
| `name`  | string | The name of the manufacturer |

### Image

| Name         | Type   | Description                  |
|--------------|--------|------------------------------|
| `url`        | string | The url of the image         |
| `default`    | bool   | Whether the image is default |
| `attributes` | array  | The attributes of the image  |

### Category

| Name         | Type   | Description                                               |
|--------------|--------|-----------------------------------------------------------|
| `id`         | int    | The id of the category                                    |
| `name`       | string | The name of the category (e.g., Coats)                    |
| `breadcrumb` | string | The breadcrumb path for the category (e.g., Mens > Coats) |

### Variant

| Name                    | Type     | Description                                                       |
|-------------------------|----------|-------------------------------------------------------------------|
| `sku`                   | string   | The **unique** SKU for the variant                                |
| `reference`             | string   | The **unique** reference for the variant                          |
| `name`                  | string   | Display name of the variant                                       |
| `summary`               | string   | A short summary of the variant                                    |
| `description`           | string   | A detailed description of the variant                             |
| `barcode`               | string   | The barcode/UPC/EAN of the variant                                |
| `buyable`               | boolean  | Whether the variant can be purchased                              |
| `visible`               | boolean  | Whether the variant is visible in listings                        |
| `shippable`             | boolean  | Whether the variant is shippable                                  |
| `discountable`          | boolean  | Whether discounts can be applied to this variant                  |
| `hide_when_no_stock`    | boolean  | Whether the variant should be hidden when out of stock            |
| `infinite_stock`        | boolean  | Whether the variant has unlimited stock                           |
| `stock_level`           | int      | Current stock level                                               |
| `stock_buffer`          | int      | The stock buffer                                                  |
| `tax_group`             | string   | The tax group applied to the variant                              |
| `minimum_quantity`      | int      | Minimum quantity per purchase                                     |
| `maximum_quantity`      | int      | Maximum quantity per purchase                                     |
| `multiples_of`          | int      | Purchasable only in multiples of this number                      |
| `weight`                | float    | Weight of the variant                                             |
| `weight_unit`           | string   | Unit of weight (e.g., `kg`, `lb`)                                 |
| `volume`                | float    | Volume of the variant                                             |
| `volume_unit`           | string   | Unit of volume (e.g., `m^3`, `cm^3`)                              |
| `hs`                    | string   | HS (Harmonized System) code for customs                           |
| `price.amount`          | float    | The current price of the variant **excluding tax**                |
| `price.tax`             | float    | The tax of the current price                                      |
| `price.currency`        | string   | The currency of the current price                                 |
| `retail.amount`         | float    | The RRP for the variant **excluding tax**                         |
| `retail.tax`            | float    | The tax of the RRP                                                |
| `retail.currency`       | string   | The currency of the RRP                                           |
| `origin_country`        | string   | ISO country code of origin (e.g., `US`, `GB`)                     |
| `goods_description`     | string   | Description of goods for customs                                  |
| `attributes`            | array    | An array of [Attribute](#attribute) objects                       |
| `tags`                  | array    | An array of [Tag](#tag) objects                                   |
| `cost`                  | object   | The [Cost Price](#cost-price) of the variant                      |
| `prices`                | array    | An array of [Price](#price) objects                               |
| `additional_attributes` | array    | An array of [Additional Attribute](#additional-attribute) objects |

### Attribute

| Name        | Type   | Description                                    |
|-------------|--------|------------------------------------------------|
| `id`        | int    | The id of the attribute                        |
| `name`      | string | The name of the attribute                      |
| `reference` | string | The reference of the attribute                 |
| `group`     | object | The [Attribute Group](#attribute-group) object |

### Attribute Group

| Name         | Type   | Description                    |
|--------------|--------|--------------------------------|
| `id`         | int    | The id of the tag group        |
| `name`       | string | The name of the tag group      |
| `reference`  | string | The reference of the tag group |

### Tag

| Name          | Type   | Description                        |
|---------------|--------|------------------------------------|
| `id`          | int    | The id of the tag                  |
| `name`        | string | The name of the tag                |
| `reference`   | string | The reference of the tag           |
| `group`       | object | The [Tag Group](#tag-group) object |

### Tag Group

| Name        | Type   | Description                    |
|-------------|--------|--------------------------------|
| `id`        | int    | The id of the tag group        |
| `name`      | string | The name of the tag group      |
| `reference` | string | The reference of the tag group |

### Cost Price

| Name       | Type   | Description                                                |
|------------|--------|------------------------------------------------------------|
| `amount`   | float  | The cost price **including tax**                           |
| `currency` | string | Currency code (defaults to store default if not provided)  |

### Price

| Name                  | Type      | Description                                                |
|-----------------------|-----------|------------------------------------------------------------|
| `id`                  | int       | The id of the price                                        |
| `currency`            | string    | The currency code for the price                            |
| `quantity`            | int       | The quantity required for the price to be detected/applied |
| `value.amount`        | float     | The normal price **excluding tax**                         |
| `value.tax`           | float     | The tax for the normal price                               |
| `sale_value.amount`   | float     | The sale price **excluding tax**                           |
| `sale_value.tax`      | float     | The tax for the sale price                                 |
| `retail_value.amount` | float     | The retail price **excluding tax**                         |
| `retail_value.tax`    | float     | The tax for the retail price                               |
| `start_at`            | timestamp | The start date for when the price is active                |
| `end_at`              | timestamp | The end date for when the price is active                  |
| `reference`           | string    | The reference for the price                                |

### SEO

| Name               | Type      | Description                |
|--------------------|-----------|----------------------------|
| `heading`          | string    | The SEO Heading            |
| `page_title`       | string    | The SEO Page Title         |
| `meta_description` | string    | The SEO Meta Description   |
| `canonical`        | string    | The SEO Canonical          |
| `noindex`          | boolean   | The SEO No Index           |
| `nofollow`         | boolean   | The SEO No Follow          |

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

| Name    | Type    | Description                           |
|---------|---------|---------------------------------------|
| `key`   | string  | The key of the additional attribute   |
| `value` | string  | The value of the additional attribute |

## Example Request

```http request
GET /api/products/{id|model}
```

## Example Response

### Simple Product

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
            "default": true
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

### Variant Product

```json lines
{
    "id": 1,
    "model": "8021182",
    "name": "Detachable Sleeve Puffer Jacket",
    "summary": "Outer: Leather 100%, Polyamide 100%\nLining: Polyester 100%, Goose Down 90%, Wool 70%, Polyamide 20%, Cashmere 10%, Feather 10%",
    "description": "A quintessentially British brand, Burberry creates iconic designs that seamlessly infuse their rich heritage with a contemporary aesthetic. This deep blue wool and cashmere blend detachable sleeve puffer jacket from Burberry features a hood, a high standing collar, a zip and press stud fastening, detachable long sleeves, a contrast logo patch to one side, zipped side slit pockets and a puffer style.",
    "type": "variant",
    "active": true,
    "visible": true,
    "attribute_groups_to_split_by": null,
    "published_at": "2025-06-13T07:34:34.000000Z",
    "manufacturer": {
        "id": 1,
        "name": "Burberry"
    },
    "images": [
        {
            "url": "https://picsum.photos/seed/first/600/400",
            "default": "1"
        },
        {
            "url": "https://picsum.photos/seed/second/600/400",
            "default": "1"
        },
        {
            "url": "https://picsum.photos/seed/third/600/400",
            "default": "1"
        },
    ],
    "categories": [
        {
            "id": 3,
            "name": "Padded Coats",
            "breadcrumb": "Mens » Coats » Padded Coats"
        }
    ],
    "tags": [
        {
            "id": 1,
            "name": "Blue",
            "reference": null,
            "group": {
                "id": 1,
                "name": "Colour",
                "reference": null
            }
        }
    ],
    "seo": {
        "heading": "test heading",
        "page_title": "test page title",
        "meta_description": "test meta description",
        "open_graph": "",
        "canonical": "",
        "noindex": null,
        "nofollow": null
    },
    "variants": [
        {
            "id": 1,
            "sku": "8021182-S",
            "reference": null,
            "name": "",
            "summary": "",
            "description": "",
            "barcode": null,
            "buyable": true,
            "visible": true,
            "shippable": true,
            "discountable": true,
            "infinite_stock": false,
            "stock_level": 5,
            "stock_buffer": 0,
            "weight": null,
            "weight_unit": null,
            "volume": null,
            "volume_unit": null,
            "hs": null,
            "origin_country": null,
            "goods_description": null,
            "cost": {
                "amount": 5623.54,
                "currency": "GBP"
            },
            "price": {
                "amount": 65833.33,
                "tax": 13166.669999999998,
                "currency": "GBP"
            },
            "retail": {
                "amount": null,
                "tax": null,
                "currency": "GBP"
            },
            "prices": [
                {
                    "id": 1,
                    "currency": "GBP",
                    "quantity": 1,
                    "value": {
                        "amount": 65833.33,
                        "tax": 13166.669999999998
                    },
                    "sale_value": {
                        "amount": 65833.33,
                        "tax": 13166.669999999998
                    },
                    "retail_value": {
                        "amount": null,
                        "tax": null
                    },
                    "start_at": null,
                    "end_at": null,
                    "reference": null
                }
            ],
            "images": [
                {
                    "url": "https://picsum.photos/seed/fourth/600/400",
                    "default": "1",
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
            "attributes": [
                {
                    "id": 1,
                    "name": "Small",
                    "display_name": "Small",
                    "reference": null,
                    "group": {
                        "id": 1,
                        "name": "Size",
                        "reference": null
                    }
                }
            ],
            "tags": [
                {
                    "id": 2,
                    "name": "Small",
                    "reference": null,
                    "group": {
                        "id": 2,
                        "name": "Size",
                        "reference": null
                    }
                }
            ],
            "additional_attributes": []
        },
        {
            "id": 2,
            "sku": "8021182-M",
            "reference": null,
            "name": "",
            "summary": "",
            "description": "",
            "barcode": null,
            "buyable": true,
            "visible": true,
            "shippable": true,
            "discountable": true,
            "infinite_stock": false,
            "stock_level": 5,
            "stock_buffer": 0,
            "weight": null,
            "weight_unit": null,
            "volume": null,
            "volume_unit": null,
            "hs": null,
            "origin_country": null,
            "goods_description": null,
            "cost": {
                "amount": null,
                "currency": null
            },
            "price": {
                "amount": 65833.33,
                "tax": 13166.669999999998,
                "currency": "GBP"
            },
            "retail": {
                "amount": null,
                "tax": null,
                "currency": "GBP"
            },
            "prices": [
                {
                    "id": 2,
                    "currency": "GBP",
                    "quantity": 1,
                    "value": {
                        "amount": 65833.33,
                        "tax": 13166.669999999998
                    },
                    "sale_value": {
                        "amount": 65833.33,
                        "tax": 13166.669999999998
                    },
                    "retail_value": {
                        "amount": null,
                        "tax": null
                    },
                    "start_at": null,
                    "end_at": null,
                    "reference": null
                }
            ],
            "images": [],
            "attributes": [
                {
                    "id": 2,
                    "name": "Medium",
                    "display_name": "Medium",
                    "reference": null,
                    "group": {
                        "id": 1,
                        "name": "Size",
                        "reference": null
                    }
                }
            ],
            "tags": [
                {
                    "id": 3,
                    "name": "Medium",
                    "reference": null,
                    "group": {
                        "id": 2,
                        "name": "Size",
                        "reference": null
                    }
                }
            ],
            "additional_attributes": []
        },
        {
            "id": 3,
            "sku": "8021182-L",
            "reference": null,
            "name": "",
            "summary": "",
            "description": "",
            "barcode": null,
            "buyable": true,
            "visible": true,
            "shippable": true,
            "discountable": true,
            "infinite_stock": false,
            "stock_level": 5,
            "stock_buffer": 0,
            "weight": null,
            "weight_unit": null,
            "volume": null,
            "volume_unit": null,
            "hs": null,
            "origin_country": null,
            "goods_description": null,
            "cost": {
                "amount": null,
                "currency": null
            },
            "price": {
                "amount": 65833.33,
                "tax": 13166.669999999998,
                "currency": "GBP"
            },
            "retail": {
                "amount": null,
                "tax": null,
                "currency": "GBP"
            },
            "prices": [
                {
                    "id": 3,
                    "currency": "GBP",
                    "quantity": 1,
                    "value": {
                        "amount": 65833.33,
                        "tax": 13166.669999999998
                    },
                    "sale_value": {
                        "amount": 65833.33,
                        "tax": 13166.669999999998
                    },
                    "retail_value": {
                        "amount": null,
                        "tax": null
                    },
                    "start_at": null,
                    "end_at": null,
                    "reference": null
                }
            ],
            "images": [],
            "attributes": [
                {
                    "id": 3,
                    "name": "Large",
                    "display_name": "Large",
                    "reference": null,
                    "group": {
                        "id": 1,
                        "name": "Size",
                        "reference": null
                    }
                }
            ],
            "tags": [
                {
                    "id": 4,
                    "name": "Large",
                    "reference": null,
                    "group": {
                        "id": 2,
                        "name": "Size",
                        "reference": null
                    }
                }
            ],
            "additional_attributes": []
        },
        {
            "id": 4,
            "sku": "8021182-XL",
            "reference": null,
            "name": "",
            "summary": "",
            "description": "",
            "barcode": null,
            "buyable": true,
            "visible": true,
            "shippable": true,
            "discountable": true,
            "infinite_stock": false,
            "stock_level": 5,
            "stock_buffer": 0,
            "weight": null,
            "weight_unit": null,
            "volume": null,
            "volume_unit": null,
            "hs": null,
            "origin_country": null,
            "goods_description": null,
            "cost": {
                "amount": null,
                "currency": null
            },
            "price": {
                "amount": 65833.33,
                "tax": 13166.669999999998,
                "currency": "GBP"
            },
            "retail": {
                "amount": null,
                "tax": null,
                "currency": "GBP"
            },
            "prices": [
                {
                    "id": 1,
                    "currency": "GBP",
                    "quantity": 1,
                    "value": {
                        "amount": 65833.33,
                        "tax": 13166.669999999998
                    },
                    "sale_value": {
                        "amount": 65833.33,
                        "tax": 13166.669999999998
                    },
                    "retail_value": {
                        "amount": null,
                        "tax": null
                    },
                    "start_at": null,
                    "end_at": null,
                    "reference": null
                }
            ],
            "images": [],
            "attributes": [
                {
                    "id": 4,
                    "name": "Extra Large",
                    "display_name": "Extra Large",
                    "reference": null,
                    "group": {
                        "id": 1,
                        "name": "Size",
                        "reference": null
                    }
                }
            ],
            "tags": [
                {
                    "id": 5,
                    "name": "Extra Large",
                    "reference": null,
                    "group": {
                        "id": 2,
                        "name": "Size",
                        "reference": null
                    }
                }
            ],
            "additional_attributes": []
        }
    ],
    "additional_attributes": [],
    "settings": []
}
```

[Back to contents](../../README.md#table-of-contents)
