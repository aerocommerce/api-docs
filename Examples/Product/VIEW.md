# View Product

## Attributes:

### Product

| Name                                | Type     | Description                                                        |
|-------------------------------------|----------|--------------------------------------------------------------------|
| `id`                                | int      | The id of the product                                              |
| `model`                             | string   | The model of the product                                           |
| `name`                              | string   | The name of the product                                            |
| `summary`                           | string   | The summary of the product                                         |
| `description`                       | string   | The description of the product                                     |
| `type`                              | string   | The type of the product                                            |
| `active`                            | boolean  | Whether the product can be purchased                               |
| `visible`                           | boolean  | Whether the product is visible on the storefront                   |
| `attribute_groups_to_split_by`      | ?array   | The attribute groups to split listings by                          |
| `published_at`                      | date     | The date that the product was published at                         |
| `manufacturer`                      | object   | The manufacturer of the product, see [Manufacturer](#manufacturer) |
| `images`                            | array    | The images of the product, see [Images](#images)                   |
| `categories`                        | array    | The categories of the product, see [Categories](#categories)       |
| `tags`                              | array    | The tags of the product, see [Tags](#tags)                         |
| `variants`                          | array    | The variants of the product, see [Variants](#variants)             |

### Manufacturer

A product can have a manufacturer, if it doesn't then `manufacturer` will be `null`, see attributes below:

| Name                | Type   | Description                  |
|---------------------|--------|------------------------------|
| `manufacturer.id`   | string | The id of the manufacturer   |
| `manufacturer.name` | string | The name of the manufacturer |

### Images

A product can have images, see attributes below:

| Name                  | Type   | Description                  |
|-----------------------|--------|------------------------------|
| `images.*.url`        | string | The url of the image         |
| `images.*.is_default` | bool   | Whether the image is default |
| `images.*.attributes` | array  | The attributes of the image  |

### Categories

A product can have categories, see attributes below:

| Name                      | Type   | Description                                             |
|---------------------------|--------|---------------------------------------------------------|
| `categories.*.id`         | int    | The id of the category                                  |
| `categories.*.name`       | string | The name of the category, e.g. coats                    |
| `categories.*.breadcrumb` | string | The breadcrumb path for the category, e.g. mens > coats |

### Tags

A product can have tags, see attributes below:

| Name               | Type   | Description                                                    |
|--------------------|--------|----------------------------------------------------------------|
| `tags.*.id`        | string | The id of the tag                                              |
| `tags.*.name`      | string | The name of the tag                                            |
| `tags.*.reference` | string | The reference of the tag                                       |
| `tags.*.group`     | object | The group that the tag belongs to, see [Tag Group](#tag-group) |

### Tag Group

A tag has a tag group, see attributes below:

| Name              | Type   | Description                    |
|-------------------|--------|--------------------------------|
| `group.id`        | string | The id of the tag group        |
| `group.name`      | string | The name of the tag group      |
| `group.reference` | string | The reference of the tag group |

### Variants

A product has variant(s), see attributes below:

| Name                           | Type    | Description                                                  |
|--------------------------------|---------|--------------------------------------------------------------|
| `variants.*.id`                | int     | The id of the variant                                        |
| `variants.*.sku`               | string  | The sku of the variant                                       |
| `variants.*.reference`         | string  | The reference of the variant                                 |
| `variants.*.name`              | string  | The name of the variant                                      |
| `variants.*.summary`           | string  | The summary of the variant                                   |
| `variants.*.description`       | string  | The description of the variant                               |
| `variants.*.barcode`           | string  | The barcode of the variant                                   |
| `variants.*.buyable`           | boolean | Whether the variant can be purchased                         |
| `variants.*.visible`           | boolean | Whether the variant is visible on the storefront             |
| `variants.*.shippable`         | boolean | Whether the variant requires shipping                        |
| `variants.*.discountable`      | boolean | Whether the variant can be discounted                        |
| `variants.*.infinite_stock`    | boolean | Whether the variant has infinite stock                       |
| `variants.*.stock_level`       | int     | The stock level of the variant                               |
| `variants.*.stock_buffer`      | int     | The stock buffer of the variant                              |
| `variants.*.weight`            | float   | The weight of the variant                                    |
| `variants.*.weight_unit`       | string  | The unit for the weight                                      |
| `variants.*.volume`            | float   | The volume of the variant                                    |
| `variants.*.volume_unit`       | string  | The unit for the volume                                      |
| `variants.*.hs`                | string  | The hs code for the variant                                  |
| `variants.*.origin_country`    | string  | The origin country code for the variant                      |
| `variants.*.goods_description` | string  | The goods description for the variant                        |
| `variants.*.cost.amount`       | float   | The cost price of the variant **excluding tax**              |
| `variants.*.cost.currency`     | string  | The currency for the cost price                              |
| `variants.*.price.amount`      | float   | The current price of the variant **excluding tax**           |
| `variants.*.price.tax`         | float   | The tax of the current price                                 |
| `variants.*.price.currency`    | string  | The currency of the current price                            |
| `variants.*.retail.amount`     | float   | The RRP for the variant **excluding tax**                    |
| `variants.*.retail.tax`        | float   | The tax of the RRP                                           |
| `variants.*.retail.currency`   | string  | The currency of the RRP                                      |
| `variants.*.prices`            | array   | The prices of the variant, see [Price](#price)               |
| `variants.*.images`            | array   | The images of the variant, see [Images](#images)             |
| `variants.*.attributes`        | array   | The attributes of the variant, see [Attributes](#attributes) |
| `variants.*.tags`              | array   | The attributes of the variant, see [Tags](#tags)             |

### Price

A variant has price(s), see attributes below:

| Name                           | Type   | Description                                                |
|--------------------------------|--------|------------------------------------------------------------|
| `prices.*.id`                  | int    | The id of the price                                        |
| `prices.*.currency`            | string | The currency code for the price                            |
| `prices.*.quantity`            | int    | The quantity required for the price to be detected/applied |
| `prices.*.value.amount`        | float  | The normal price **excluding tax**                         |
| `prices.*.value.tax`           | float  | The tax for the normal price                               |
| `prices.*.sale_value.amount`   | float  | The sale price **excluding tax**                           |
| `prices.*.sale_value.tax`      | float  | The tax for the sale price                                 |
| `prices.*.retail_value.amount` | float  | The retail price **excluding tax**                         |
| `prices.*.retail_value.tax`    | float  | The tax for the retail price                               |
| `prices.*.start_at`            | date   | The start date for when the price is active                |
| `prices.*.end_at`              | date   | The end date for when the price is active                  |
| `prices.*.reference`           | string | The reference for the price                                |

### Attributes

A variant can have attributes, see attributes below:

| Name                     | Type   | Description                                                                        |
|--------------------------|--------|------------------------------------------------------------------------------------|
| `attributes.*.id`        | string | The id of the attribute                                                            |
| `attributes.*.name`      | string | The name of the attribute                                                          |
| `attributes.*.reference` | string | The reference of the attribute                                                     |
| `attributes.*.group`     | object | The group that the attribute belongs to, see [Attribute Group](#attribute-group)   |

### Attribute Group

An attribute has an attribute group, see attributes below:

| Name              | Type   | Description                    |
|-------------------|--------|--------------------------------|
| `group.id`        | string | The id of the tag group        |
| `group.name`      | string | The name of the tag group      |
| `group.reference` | string | The reference of the tag group |

## Example Response

```http request
GET /api/products/{id}
```

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
            "url": "http://l11.test/storage/images/combinations/cwKh1ghevZp7r8HgK4qyVTmrRYRwgv0qMEZzvbuo.jpg",
            "default": true,
            "attributes": []
        },
        {
            "url": "http://l11.test/storage/images/products/PBjYqxoTxjX1Waj9tAqhmMFH0dakhuJGVkl2QpQ0.jpg",
            "default": true,
            "attributes": []
        },
        {
            "url": "http://l11.test/storage/images/products/lDc5Fkxb9rlMiy6gZmysVbZPzGISBgQDGZKOoHc7.jpg",
            "default": true,
            "attributes": []
        },
        {
            "url": "http://l11.test/storage/images/products/ZJ7WgzLpxO1JAB0AvJxJYQUjiYBcvu9tpWJTNmLk.jpg",
            "default": true,
            "attributes": []
        }
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
        "heading": "",
        "page_title": "",
        "meta_description": "",
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
                    "id": 4,
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
