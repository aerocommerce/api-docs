# Product Index

## Attributes:

See [View Product](VIEW.md)

## Remarks

This is a paginated route (see [Pagination Conventions](../../CONVENTIONS.md#pagination-conventions))

In addition to the standard parameters accepted for a paginated route, this route also accepts:

| Parameter        | Description                        | Example                                 |
|------------------|------------------------------------|-----------------------------------------|
| `min_updated_at` | The min updated at for a product   | ?min_updated_at=2023-08-30%2010:35:05   |
| `max_updated_at` | The max updated at for a product   | ?max_updated_at=2023-08-30%2010:35:05   |

see [Date Conventions](../../CONVENTIONS.md#date-conventions) for more info on acceptable values for these parameters

## Example Response

```http request
GET /api/products?per_page=2&min_updated_at=2023-08-30%2010:36:23
```

```json lines
{
    "current_page": 1,
    "data": [
        {
            "id": 1,
            "model": "8021182",
            "name": "Detachable Sleeve Puffer Jacket",
            "summary": "Outer: Leather 100%, Polyamide 100%\r\nLining: Polyester 100%, Goose Down 90%, Wool 70%, Polyamide 20%, Cashmere 10%, Feather 10%",
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
                        "currency": "GBP"
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
                        "currency": "GBP"
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
                    ],
                    "tags": []
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
                        "currency": "GBP"
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
                    ],
                    "tags": []
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
                        "currency": "GBP"
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
                    ],
                    "tags": []
                }
            ]
        },
        {
            "id": 10,
            "model": "419078568950",
            "name": "Logo Patch Padded Jacket",
            "summary": "Polyamide 100%\r\nLining: Goose Down 90%, Feather 10%",
            "description": "The jacket you need for apr\u00e8s-ski. This red logo patch padded jacket from Moncler proves why they are masters of cold-weather clothing. Outdo everyone else's puffer jacket efforts. Featuring a hood, a stand up collar, a front zip fastening, long sleeves, elasticated cuffs, side pockets and patch details.",
            "type": "variant",
            "published_at": "2023-08-30T10:35:23.000000Z",
            "manufacturer": {
                "id": 5,
                "name": "Moncler"
            },
            "images": [
                {
                    "url": "http:\/\/seg.test\/images\/products\/rqvrgNBkHzBd2BB5LqFLwfQeuBJ5UTeoNiFF7rrl.png"
                }
            ],
            "categories": [
                {
                    "id": 7,
                    "name": "Padded & Down Jackets",
                    "breadcrumb": "Mens \u00bb Jackets \u00bb Padded & Down Jackets"
                }
            ],
            "tags": [],
            "variants": [
                {
                    "id": 39,
                    "sku": "419078568950-R-S",
                    "reference": null,
                    "name": "",
                    "summary": "",
                    "description": "",
                    "barcode": null,
                    "infinite_stock": false,
                    "stock_level": 1,
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 39,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/c42vDMfbRAU2nI4wrErl0hrJGjfCxDMuY4D5E3pd.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/YA4C9nzG95PWzEGxPXAfZfKlm3g7cCqXPnzAlga3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/Tr2uxBrrAyQ9b9MbAN7DMWDabHboK2E08utMFwY2.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/uBtzO0BiWFUi97oc1aoOUr0G5sWspz4J0Afz5IUN.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/OiYZWPCJyk2eW6ek5A02gr4JCkyKCzbmrnjk2I5s.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/W1tcHBSWHeXn7bG48jQYyuY5YlZJi8tTMauzXvd3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/Ys25VKr7ecxdPCFexnJWgBlf3wDtao9suDK0mHVb.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 11,
                            "name": "Red",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 8,
                            "name": "1",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 43,
                    "sku": "419078568950-DB-S",
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 43,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/SPGtImVvVOEl1CY4u5qadRAuBNbf8gx7Qe3BOaML.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/sXQHJ6a9aW6A2GE2C8u0qH8PonMMcNeP1lYZU9N2.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/9rmIupLpShzTlMNpcxdqk0TpndrhGrxOFDftnbhe.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/60zvpw9EgROc9RdC85PfUxCA3ThPg8e7Twg1mZZZ.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/H4WIH0PJoRNSx3JQ2JdMExHo3ytUHPinSV9Uetn6.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/PbNdni91HhhC5EbFebmarAdMRZPnGqCBYjLXT44c.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/uyMGFO1fcglNSqyPl2iPZESTOkCNV45ES5PfxXLV.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 14,
                            "name": "Dark Blue",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 8,
                            "name": "1",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 47,
                    "sku": "419078568950-BG-S",
                    "reference": null,
                    "name": "",
                    "summary": "",
                    "description": "",
                    "barcode": null,
                    "infinite_stock": false,
                    "stock_level": 3,
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 47,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/WnsmIpB2YjlvhSlx7xURyT2YCjS5pcGO6YVT9xyy.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/7qHMqSSQxDwBA8Ze4x0r5SM0h3p9iBKhm4a7a56a.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/bzUYbxwUEf5QnZCkm8knIu9fDkHUyeI5rWJ30h0i.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/l5goRZVH9a4k70RAsqap3ykvyMBCpKkISx85eBkV.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/dznUyxZodnFoKehjEy4S944XS6GkMgp1raJdS91p.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/LLW3nfBW0C70dFyBMd0kmLeeTYFUSsr6KK23Oft3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/noULALOZvVm52MhgS0ZDrRQ4rYwfqBhfDxirHGrh.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 15,
                            "name": "Blue \/ Green",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 8,
                            "name": "1",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 40,
                    "sku": "419078568950-R-M",
                    "reference": null,
                    "name": "",
                    "summary": "",
                    "description": "",
                    "barcode": null,
                    "infinite_stock": false,
                    "stock_level": 3,
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 40,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/c42vDMfbRAU2nI4wrErl0hrJGjfCxDMuY4D5E3pd.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/YA4C9nzG95PWzEGxPXAfZfKlm3g7cCqXPnzAlga3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/Tr2uxBrrAyQ9b9MbAN7DMWDabHboK2E08utMFwY2.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/uBtzO0BiWFUi97oc1aoOUr0G5sWspz4J0Afz5IUN.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/OiYZWPCJyk2eW6ek5A02gr4JCkyKCzbmrnjk2I5s.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/W1tcHBSWHeXn7bG48jQYyuY5YlZJi8tTMauzXvd3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/Ys25VKr7ecxdPCFexnJWgBlf3wDtao9suDK0mHVb.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 11,
                            "name": "Red",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 9,
                            "name": "2",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 44,
                    "sku": "419078568950-DB-M",
                    "reference": null,
                    "name": "",
                    "summary": "",
                    "description": "",
                    "barcode": null,
                    "infinite_stock": false,
                    "stock_level": 3,
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 44,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/SPGtImVvVOEl1CY4u5qadRAuBNbf8gx7Qe3BOaML.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/sXQHJ6a9aW6A2GE2C8u0qH8PonMMcNeP1lYZU9N2.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/9rmIupLpShzTlMNpcxdqk0TpndrhGrxOFDftnbhe.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/60zvpw9EgROc9RdC85PfUxCA3ThPg8e7Twg1mZZZ.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/H4WIH0PJoRNSx3JQ2JdMExHo3ytUHPinSV9Uetn6.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/PbNdni91HhhC5EbFebmarAdMRZPnGqCBYjLXT44c.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/uyMGFO1fcglNSqyPl2iPZESTOkCNV45ES5PfxXLV.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 14,
                            "name": "Dark Blue",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 9,
                            "name": "2",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 48,
                    "sku": "419078568950-BG-M",
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 48,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/WnsmIpB2YjlvhSlx7xURyT2YCjS5pcGO6YVT9xyy.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/7qHMqSSQxDwBA8Ze4x0r5SM0h3p9iBKhm4a7a56a.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/bzUYbxwUEf5QnZCkm8knIu9fDkHUyeI5rWJ30h0i.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/l5goRZVH9a4k70RAsqap3ykvyMBCpKkISx85eBkV.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/dznUyxZodnFoKehjEy4S944XS6GkMgp1raJdS91p.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/LLW3nfBW0C70dFyBMd0kmLeeTYFUSsr6KK23Oft3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/noULALOZvVm52MhgS0ZDrRQ4rYwfqBhfDxirHGrh.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 15,
                            "name": "Blue \/ Green",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 9,
                            "name": "2",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 41,
                    "sku": "419078568950-R-L",
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 41,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/c42vDMfbRAU2nI4wrErl0hrJGjfCxDMuY4D5E3pd.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/YA4C9nzG95PWzEGxPXAfZfKlm3g7cCqXPnzAlga3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/Tr2uxBrrAyQ9b9MbAN7DMWDabHboK2E08utMFwY2.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/uBtzO0BiWFUi97oc1aoOUr0G5sWspz4J0Afz5IUN.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/OiYZWPCJyk2eW6ek5A02gr4JCkyKCzbmrnjk2I5s.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/W1tcHBSWHeXn7bG48jQYyuY5YlZJi8tTMauzXvd3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/Ys25VKr7ecxdPCFexnJWgBlf3wDtao9suDK0mHVb.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 11,
                            "name": "Red",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 10,
                            "name": "3",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 45,
                    "sku": "419078568950-DB-L",
                    "reference": null,
                    "name": "",
                    "summary": "",
                    "description": "",
                    "barcode": null,
                    "infinite_stock": false,
                    "stock_level": 1,
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 45,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/SPGtImVvVOEl1CY4u5qadRAuBNbf8gx7Qe3BOaML.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/sXQHJ6a9aW6A2GE2C8u0qH8PonMMcNeP1lYZU9N2.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/9rmIupLpShzTlMNpcxdqk0TpndrhGrxOFDftnbhe.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/60zvpw9EgROc9RdC85PfUxCA3ThPg8e7Twg1mZZZ.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/H4WIH0PJoRNSx3JQ2JdMExHo3ytUHPinSV9Uetn6.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/PbNdni91HhhC5EbFebmarAdMRZPnGqCBYjLXT44c.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/uyMGFO1fcglNSqyPl2iPZESTOkCNV45ES5PfxXLV.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 14,
                            "name": "Dark Blue",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 10,
                            "name": "3",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 49,
                    "sku": "419078568950-BG-L",
                    "reference": null,
                    "name": "",
                    "summary": "",
                    "description": "",
                    "barcode": null,
                    "infinite_stock": false,
                    "stock_level": 1,
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 49,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/WnsmIpB2YjlvhSlx7xURyT2YCjS5pcGO6YVT9xyy.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/7qHMqSSQxDwBA8Ze4x0r5SM0h3p9iBKhm4a7a56a.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/bzUYbxwUEf5QnZCkm8knIu9fDkHUyeI5rWJ30h0i.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/l5goRZVH9a4k70RAsqap3ykvyMBCpKkISx85eBkV.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/dznUyxZodnFoKehjEy4S944XS6GkMgp1raJdS91p.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/LLW3nfBW0C70dFyBMd0kmLeeTYFUSsr6KK23Oft3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/noULALOZvVm52MhgS0ZDrRQ4rYwfqBhfDxirHGrh.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 15,
                            "name": "Blue \/ Green",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 10,
                            "name": "3",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 42,
                    "sku": "419078568950-R-XL",
                    "reference": null,
                    "name": "",
                    "summary": "",
                    "description": "",
                    "barcode": null,
                    "infinite_stock": false,
                    "stock_level": 1,
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 42,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/c42vDMfbRAU2nI4wrErl0hrJGjfCxDMuY4D5E3pd.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/YA4C9nzG95PWzEGxPXAfZfKlm3g7cCqXPnzAlga3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/Tr2uxBrrAyQ9b9MbAN7DMWDabHboK2E08utMFwY2.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/uBtzO0BiWFUi97oc1aoOUr0G5sWspz4J0Afz5IUN.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/OiYZWPCJyk2eW6ek5A02gr4JCkyKCzbmrnjk2I5s.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/W1tcHBSWHeXn7bG48jQYyuY5YlZJi8tTMauzXvd3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/Ys25VKr7ecxdPCFexnJWgBlf3wDtao9suDK0mHVb.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 11,
                            "name": "Red",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 12,
                            "name": "4",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 46,
                    "sku": "419078568950-DB-XL",
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 46,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/SPGtImVvVOEl1CY4u5qadRAuBNbf8gx7Qe3BOaML.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/sXQHJ6a9aW6A2GE2C8u0qH8PonMMcNeP1lYZU9N2.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/9rmIupLpShzTlMNpcxdqk0TpndrhGrxOFDftnbhe.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/60zvpw9EgROc9RdC85PfUxCA3ThPg8e7Twg1mZZZ.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/H4WIH0PJoRNSx3JQ2JdMExHo3ytUHPinSV9Uetn6.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/PbNdni91HhhC5EbFebmarAdMRZPnGqCBYjLXT44c.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/uyMGFO1fcglNSqyPl2iPZESTOkCNV45ES5PfxXLV.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 14,
                            "name": "Dark Blue",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 12,
                            "name": "4",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                },
                {
                    "id": 50,
                    "sku": "419078568950-BG-XL",
                    "reference": null,
                    "name": "",
                    "summary": "",
                    "description": "",
                    "barcode": null,
                    "infinite_stock": false,
                    "stock_level": 0,
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
                        "currency": "GBP"
                    },
                    "price": {
                        "amount": 84583.33,
                        "tax": 16916.67,
                        "currency": "GBP"
                    },
                    "retail": {
                        "amount": 0,
                        "tax": 0,
                        "currency": "GBP"
                    },
                    "prices": [
                        {
                            "id": 50,
                            "currency": "GBP",
                            "quantity": 1,
                            "value": {
                                "amount": 101500
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
                    "images": [
                        {
                            "url": "http:\/\/seg.test\/images\/products\/WnsmIpB2YjlvhSlx7xURyT2YCjS5pcGO6YVT9xyy.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/7qHMqSSQxDwBA8Ze4x0r5SM0h3p9iBKhm4a7a56a.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/bzUYbxwUEf5QnZCkm8knIu9fDkHUyeI5rWJ30h0i.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/l5goRZVH9a4k70RAsqap3ykvyMBCpKkISx85eBkV.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/dznUyxZodnFoKehjEy4S944XS6GkMgp1raJdS91p.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/LLW3nfBW0C70dFyBMd0kmLeeTYFUSsr6KK23Oft3.jpg"
                        },
                        {
                            "url": "http:\/\/seg.test\/images\/products\/noULALOZvVm52MhgS0ZDrRQ4rYwfqBhfDxirHGrh.jpg"
                        }
                    ],
                    "attributes": [
                        {
                            "id": 15,
                            "name": "Blue \/ Green",
                            "reference": null,
                            "group": {
                                "id": 2,
                                "name": "Colour",
                                "reference": null
                            }
                        },
                        {
                            "id": 12,
                            "name": "4",
                            "reference": null,
                            "group": {
                                "id": 1,
                                "name": "Size",
                                "reference": null
                            }
                        }
                    ],
                    "tags": []
                }
            ]
        }
    ],
    "first_page_url": "http:\/\/seg.test\/api\/products?page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http:\/\/seg.test\/api\/products?page=3",
    "next_page_url": "http:\/\/seg.test\/api\/products?page=2",
    "path": "http:\/\/seg.test\/api\/products",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```


