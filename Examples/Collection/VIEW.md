# View Collection

## Overview

This endpoint retrieves a single collection by `id` or `name`

## Structure

### Collection

| Name                    | Type   | Description                                                                                       | 
|-------------------------|--------|---------------------------------------------------------------------------------------------------|
| `name`                  | string | The name of the collection                                                                        |
| `slug`                  | string | The slug of the collection                                                                        |
| `reference`             | string | The reference of the collection                                                                   |
| `logic`                 | string | The logic of the rules for the collection                                                         |
| `rules`                 | array  | The listing page rules of the collection, see [Rule](#rule)                                       |
| `content`               | object | The listing page content of the collection, see [Content](#content)                               |
| `options`               | object | The listing page options of the collection, see [Options](#options)                               |
| `seo`                   | object | The SEO of the collection, see [SEO](#seo)                                                        |
| `additional_attributes` | array  | The additional attributes of the collection, see [Additional Attribute](#additional-attribute)    |

### Image

| Name  | Type   | Description          |
|-------|--------|----------------------|
| `url` | string | The url of the image |

### Tag

| Name       | Type   | Description                                |
|------------|--------|--------------------------------------------|
| `name`     | string | The name of the tag (e.g., Small or Red)   |
| `group`    | object | The tag group, see [Tag Group](#tag-group) |

### Tag Group

| Name      | Type   | Description                                      |
|-----------|--------|--------------------------------------------------|
| `name`    | string | The name of the tag group (e.g., Size or Colour) |

### Rule

| Name                        | Type      | Description                                                                                      |
|-----------------------------|-----------|--------------------------------------------------------------------------------------------------|
| `type`                      | string    | The type of the rule                                                                             |
| `requirement`               | string    | The requirement of the rule                                                                      |
| `logic`                     | string    | The logic of the rule                                                                            |
| `data`                      | object    | The data for the rule, required keys vary based on `type` of the rule                            |
| `data.tags`                 | array     | An array of [Tag](#tag) objects for a `have_tags` rule                                           |
| `data.manufacturers.*.id`   | int       | The manufacturer id for a `have_manufacturers` rule                                              |
| `data.manufacturers.*.name` | string    | The manufacturer name for a `have_manufacturers` rule                                            |
| `data.price_list.id`        | int       | The price list id for an `in_price_list` rule                                                    |
| `data.price_list.name`      | string    | The price list name for an `in_price_list` rule                                                  |
| `data.category.id`          | int       | The category id for an `in_category` rule                                                        |
| `data.category.name`        | string    | The category name for an `in_category` rule                                                      |
| `data.days`                 | int       | The days for a `published_within_days` rule                                                      |
| `data.start_at`             | timestamp | The start at date for a `published_within` rule                                                  |
| `data.end_at`               | timestamp | The end at date for a `published_within` rule                                                    |
| `data.min_price`            | float     | The min price **including tax**, in whole units (e.g. pounds not pence) for `price_between` rule |
| `data.max_price`            | float     | The max price **including tax**, in whole units (e.g. pounds not pence) for `price_between` rule |
| `data.currency`             | string    | The currency code for `price_between` rule                                                       |

### Content

| Name           | Type   | Description                |
|----------------|--------|----------------------------|
| `summary`      | string | The summary content        |
| `description`  | string | The description content    |
| `small_image`  | object | The Small [Image](#image)  |
| `medium_image` | object | The Medium [Image](#image) |
| `large_image`  | object | The Large [Image](#image)  |

### Options

| Name                          | Type     | Description                                                                                                |
|-------------------------------|----------|------------------------------------------------------------------------------------------------------------|
| `categories.mode`             | string   | The category filters mode (e.g., show_all/hide_all/show_some)                                              |
| `categories.values`           | array    | The options for categories on the listings page                                                            |
| `categories.values.*.id`      | int      | The id of category                                                                                         |
| `categories.values.*.name`    | string   | The name of category                                                                                       |
| `filters.mode`                | int      | The facet filters mode (e.g., show_all/hide_all/show_some)                                                 |
| `filters.values`              | array    | The options for facet filters on the listings page                                                         |
| `filters.values.*.name`       | string   | The name of the facet filter, e.g. Manufacturer, Price, etc...                                             |
| `filters.values.*.collapsed`  | boolean  | Whether to collapse the facet filter or not                                                                |
| `sort_bys`                    | array    | An array of the applied sorts on the listings page (e.g., name-az, name-za, price-low, price-high, etc...) |
| `per_page`                    | int      | The per page of the listings page                                                                          |

### SEO

| Name               | Type      | Description                |
|--------------------|-----------|----------------------------|
| `heading`          | string    | The SEO Heading            |
| `page_title`       | string    | The SEO Page Title         |
| `meta_description` | string    | The SEO Meta Description   |
| `canonical`        | string    | The SEO Canonical          |
| `noindex`          | boolean   | The SEO No Index           |
| `nofollow`         | boolean   | The SEO No Follow          |

### Additional Attribute

| Name    | Type    | Description                           |
|---------|---------|---------------------------------------|
| `key`   | string  | The key of the additional attribute   |
| `value` | string  | The value of the additional attribute |

## Example Response

```http request
GET /api/collections/{id|name}
```

```json
{
    "id": 1,
    "name": "Sale",
    "reference": null,
    "slug": "sale",
    "published_at": "2025-01-08T12:28:14.000000Z",
    "content": {
        "summary": "Combination Summary",
        "description": "Combination Description",
        "small_image": {
            "url": null
        },
        "medium_image": {
            "url": null
        },
        "large_image": {
            "url": null
        }
    },
    "rules": [],
    "options": {
        "categories": {
            "mode": "show_all",
            "values": []
        },
        "filters": {
            "mode": "show_all",
            "values": []
        },
        "sort_bys": [],
        "per_page": 24
    },
    "seo": {
        "heading": "SEO Heading",
        "page_title": "SEO Page Title",
        "meta_description": "SEO Meta Description",
        "open_graph": "",
        "canonical": "",
        "noindex": 0,
        "nofollow": 0
    },
    "settings": [],
    "additional_attributes": []
}
```

[Back to contents](../../README.md#table-of-contents)
