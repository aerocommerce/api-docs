# View Product

## Attributes

| Name           | Type   | Description                                                                       |
|----------------|--------|-----------------------------------------------------------------------------------|
| `id`           | int    | The id of the product                                                             |
| `model`        | string | The model of the product                                                          |
| `name`         | string | The name of the product                                                           |
| `summary`      | string | The summary of the product                                                        |
| `description`  | string | The description of the product                                                    |
| `type`         | string | The type of the product                                                           |
| `published_at` | date   | The date that the product was published at                                        |
| `manufacturer` | object | The manufacturer of the product, see [View Manufacturer](../Manufacturer/VIEW.md) |
| `images`       | array  | The images of the product, see [View Image](../Image/VIEW.md)                     |
| `categories`   | array  | The categories of the product, see [View Category](../Category/VIEW.md)           |
| `tags`         | array  | The tags of the product, see [View Tag](../Tag/VIEW.md)                           |
| `variants`     | array  | The variants of the product, see [View Variant](../Variant/VIEW.md)               |

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
    "published_at": "2023-08-30T10:35:03.000000Z",
    "manufacturer": {
        "id": 1,
        "name": "Burberry"
    },
    "images": [
        {
            "url": "http:\/\/seg.test\/images\/products\/mNPSK2xf98t6ibTaw05UlSTxClxtTS6FNjybFu8r.jpg"
        },
        {
            "url": "http:\/\/seg.test\/images\/products\/tDGk08ZHtemSzVNVwncboWqqHVxs3Gdug6oVCX2G.jpg"
        },
        {
            "url": "http:\/\/seg.test\/images\/products\/yDSBv5e1FQsM9V5qB5ErqYWVu8zDDz2OTeBjr51M.jpg"
        },
        {
            "url": "http:\/\/seg.test\/images\/products\/ktZXNJxrEWd4UrbPnKqabF8ir2rnH9PUKbEFyyoa.jpg"
        }
    ],
    "categories": [
        {
            "id": 3,
            "name": "Padded Coats",
            "breadcrumb": "Mens \u00bb Coats \u00bb Padded Coats"
        }
    ],
    "tags": [
        {
            "id": 5,
            "name": "Blue",
            "reference": null,
            "group": {
                "id": 2,
                "name": "Colour",
                "reference": null
            }
        }
    ],
    "variants": [
        {
            "id": 1,
            "sku": "8021182-S",
            "reference": null,
            "name": "",
            "summary": "",
            "description": "",
            "barcode": null,
            "infinite_stock": false,
            "stock_level": 4,
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
                "amount": 0,
                "tax": 0,
                "currency": "GBP"
            },
            "prices": [
                {
                    "id": 1,
                    "currency": "GBP",
                    "quantity": 1,
                    "value": {
                        "amount": 79000
                    },
                    "sale_value": {
                        "amount": null
                    },
                    "retail_value": {
                        "amount": null
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
                    "reference": null,
                    "group": {
                        "id": 1,
                        "name": "Size",
                        "reference": null
                    }
                }
            ]
        },
        {
            "id": 2,
            "sku": "8021182-M",
            "reference": null,
            "name": "",
            "summary": "",
            "description": "",
            "barcode": null,
            "infinite_stock": false,
            "stock_level": 2,
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
                "amount": 0,
                "tax": 0,
                "currency": "GBP"
            },
            "prices": [
                {
                    "id": 2,
                    "currency": "GBP",
                    "quantity": 1,
                    "value": {
                        "amount": 79000
                    },
                    "sale_value": {
                        "amount": null
                    },
                    "retail_value": {
                        "amount": null
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
                    "reference": null,
                    "group": {
                        "id": 1,
                        "name": "Size",
                        "reference": null
                    }
                }
            ]
        },
        {
            "id": 3,
            "sku": "8021182-L",
            "reference": null,
            "name": "",
            "summary": "",
            "description": "",
            "barcode": null,
            "infinite_stock": false,
            "stock_level": 4,
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
                "amount": 0,
                "tax": 0,
                "currency": "GBP"
            },
            "prices": [
                {
                    "id": 3,
                    "currency": "GBP",
                    "quantity": 1,
                    "value": {
                        "amount": 79000
                    },
                    "sale_value": {
                        "amount": null
                    },
                    "retail_value": {
                        "amount": null
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
                    "reference": null,
                    "group": {
                        "id": 1,
                        "name": "Size",
                        "reference": null
                    }
                }
            ]
        },
        {
            "id": 4,
            "sku": "8021182-XL",
            "reference": null,
            "name": "",
            "summary": "",
            "description": "",
            "barcode": null,
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
                "amount": 0,
                "tax": 0,
                "currency": "GBP"
            },
            "prices": [
                {
                    "id": 4,
                    "currency": "GBP",
                    "quantity": 1,
                    "value": {
                        "amount": 79000
                    },
                    "sale_value": {
                        "amount": null
                    },
                    "retail_value": {
                        "amount": null
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
                    "reference": null,
                    "group": {
                        "id": 1,
                        "name": "Size",
                        "reference": null
                    }
                }
            ]
        }
    ]
}
```
