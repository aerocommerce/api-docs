# Update Product

## Overview

This endpoint updates an existing product by its `id` or `model`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Product
| Name                           | Type      | Description                                                            | Required? |
|--------------------------------|-----------|------------------------------------------------------------------------|-----------|
| `name`                         | string    | The name of the product                                                | No        |
| `manufacturer`                 | string    | The manufacturer of the product                                        | No        |
| `summary`                      | string    | The summary of the product                                             | No        |
| `description`                  | string    | The description of the product                                         | No        |
| `active`                       | boolean   | Whether the product is active                                          | No        |
| `visible`                      | boolean   | Whether the product is visible                                         | No        |
| `attribute_groups_to_split_by` | array     | An array of attribute group names to split listings by (e.g., ["Size"] | No        |
| `published_at`                 | timestamp | When the product was published                                         | No        |
| `images`                       | array     | An array of [Image](#image) objects                                    | No        |
| `categories`                   | array     | An array of [Category](#category) objects                              | No        |
| `tags`                         | array     | An array of [Tag](#tag) objects                                        | No        |
| `variants`                     | array     | An array of [Variant](#variant) objects                                | No        |
| `seo`                          | object    | A [SEO](#seo) object                                                   | No        |
| `settings`                     | object    | A [Settings](#settings) object with grouped key-value pairs            | No        |
| `additional_attributes`        | array     | An array of [Additional Attribute](#additional-attribute) objects      | No        |
| `related_listings`             | array     | An array of [Related Listing](#related-listing) objects                | No        |
### Category

| Name                    | Type      | Description                                                         | Required? |
|-------------------------|-----------|---------------------------------------------------------------------|-----------|
| `name`                  | string    | The category name or breadcrumb (e.g., "Coats" or "Mens > "Coats")  | Yes       |

### Variant

| Name                    | Type    | Description                                                           | Required? |
|-------------------------|---------|-----------------------------------------------------------------------|-----------|
| `sku`                   | string  | The **unique** SKU for the variant to be updated                      | Yes       |
| `reference`             | string  | The **unique** reference for the variant                              | No        |
| `name`                  | string  | Display name of the variant                                           | No        |
| `summary`               | string  | A short summary of the variant                                        | No        |
| `description`           | string  | A detailed description of the variant                                 | No        |
| `barcode`               | string  | The barcode/UPC/EAN of the variant                                    | No        |
| `buyable`               | boolean | Whether the variant can be purchased                                  | No        |
| `visible`               | boolean | Whether the variant is visible in listings                            | No        |
| `shippable`             | boolean | Whether the variant is shippable                                      | No        |
| `discountable`          | boolean | Whether discounts can be applied to this variant                      | No        |
| `hide_when_no_stock`    | boolean | Whether the variant should be hidden when out of stock                | No        |
| `infinite_stock`        | boolean | Whether the variant has unlimited stock                               | No        |
| `stock_level`           | int     | Current stock level                                                   | No        |
| `stock_buffer`          | int     | The stock buffer                                                      | No        |
| `stock_action`          | string  | The stock action (e.g., set, add, remove & multiply). Defaults to set | No        |
| `tax_group`             | string  | The tax group applied to the variant                                  | No        |
| `minimum_quantity`      | int     | Minimum quantity per purchase                                         | No        |
| `maximum_quantity`      | int     | Maximum quantity per purchase                                         | No        |
| `multiples_of`          | int     | Purchasable only in multiples of this number                          | No        |
| `weight`                | float   | Weight of the variant                                                 | No        |
| `weight_unit`           | string  | Unit of weight (e.g., `kg`, `lb`)                                     | No        |
| `volume`                | float   | Volume of the variant                                                 | No        |
| `volume_unit`           | string  | Unit of volume (e.g., `m^3`, `cm^3`)                                  | No        |
| `hs`                    | string  | HS (Harmonized System) code for customs                               | No        |
| `origin_country`        | string  | ISO country code of origin (e.g., `US`, `GB`)                         | No        |
| `goods_description`     | string  | Description of goods for customs                                      | No        |
| `tags`                  | array   | An array of [Tag](#tag) objects                                       | No        |
| `cost`                  | object  | The [Cost Price](#cost-price) of the variant                          | No        |
| `prices`                | array   | An array of [Price](#price) objects                                   | No        |
| `additional_attributes` | array   | An array of [Additional Attribute](#additional-attribute) objects     | No        |

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

### 1. Update Basic Product Details

```http request
PUT /api/products/{id|model}
```

```json lines
{
    "name": "Detachable Sleeve Puffer Jacket v2",
    "manufacturer": "Burberry v2",
    "summary": "A lightweight puffer with removable sleeves.",
    "description": "This updated puffer jacket offers versatility with detachable sleeves, premium fill, and water-resistant fabric.",
    "active": true,
    "visible": true
}
```

### 2. Add Categories To Product

```http request
PUT /api/products/{id|model}
```

```json lines
{
    "categories": [
        { 
            "name": "Mens > Jackets",
        },
        { 
            "name": "Winter Collection"
        }
    ]
}
```

### 3. Add Tags To Product

```http request
PUT /api/products/{id|model}
```

```json lines
{
    "tags": [
        {
            "group": {
                "name": "Colour"
            },
            "name": "Indigo"
        },
        {
            "group": {
                "name": "Season"
            },
            "name": "Winter 2023"
        }
    ]
}
```

### 4. Update Variant By Sku

```http request
PUT /api/products/{id|model}
```

```json lines
{
    "variants": [
        {
            "sku": "9021182-S",
            "stock_level": 50,
            "buyable": true,
            "tags": [
                {
                    "group": {
                        "name": "Style"
                    },
                    "name": "Casual"
                }
            ],
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
    ]
}
```

**NOTE:** It is recommended to use the [Store Variant](../Variant/STORE.md) endpoint when updating just one variant

### 5. Update Images

```http request
PUT /api/products/{id|model}
```

```json lines
{
    "images": [
        {
            "src": "https://picsum.photos/seed/front/600/400",
            "alt": "Front view of detachable sleeve puffer jacket",
            "is_default": true,
            "position": 1
        },
        {
            "src": "https://picsum.photos/seed/back/600/400",
            "alt": "Back view of detachable sleeve puffer jacket",
            "position": 2
        }
    ]
}
```

### 6. Update Product SEO & Settings

```http request
PUT /api/products/{id|model}
```

OR

```http request
PUT /api/products?model=model
```


```json lines
{
    "seo": {
        "heading": "Detachable Sleeve Puffer Jacket",
        "page_title": "Men’s Detachable Sleeve Puffer Jacket | Burberry",
        "meta_description": "Shop the Burberry detachable sleeve puffer jacket – versatile winterwear with premium fill and removable sleeves.",
        "canonical": "https://shop.example.com/mens/detachable-sleeve-puffer",
        "noindex": false,
        "nofollow": false
    },
    "settings": {
        "_": {
            "featured": "true"
        },
        "shipping": {
            "oversized": "false"
        }
    }
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
