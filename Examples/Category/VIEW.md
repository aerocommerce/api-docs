# View Category

## Overview

This endpoint retrieves a single category by `id`, `name` or `breadcrumb` (e.g., Mens > Coats)

## Structure

### Category

| Name                     | Type     | Description                                                                       |
|--------------------------|----------|-----------------------------------------------------------------------------------|
| `name`                   | string   | The name of the category                                                          |
| `parent`                 | string   | The parent of the category                                                        |
| `slug`                   | string   | The slug of the category, if not present it is auto-generated from name           |
| `reference`              | string   | The reference of the category                                                     |
| `logic`                  | string   | The logic of the rules for the category, and/or (defaults to or if not provided)  |
| `visible`                | boolean  | The visibility of the category (defaults to `true`)                               |
| `featured_image`         | object   | The [Image](#image) of the category                                               |
| `tags`                   | array    | An array of [Tag](#tag) objects                                                   |
| `rules`                  | array    | An array of Listing Page [Rule](#rule) objects                                    |
| `content`                | object   | The Listing Page [Content](#content) of the category                              |
| `options`                | object   | The Listing Page [Options](#options) of the category                              |
| `seo`                    | object   | The [SEO](#seo) of the category                                                   |
| `additional_attributes`  | array    | An array of [Additional Attribute](#additional-attribute) objects                 |

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

| Name                        | Type       | Description                                                                                      |
|-----------------------------|------------|--------------------------------------------------------------------------------------------------|
| `type`                      | string     | The type of the rule                                                                             |
| `requirement`               | string     | The requirement of the rule                                                                      |
| `logic`                     | string     | The logic of the rule                                                                            |
| `data`                      | object     | The data for the rule, required keys vary based on `type` of the rule                            |
| `data.tags`                 | array      | An array of [Tag](#tag) objects for a `have_tags` rule                                           |
| `data.manufacturers.*.id`   | int        | The manufacturer id for a `have_manufacturers` rule                                              |
| `data.manufacturers.*.name` | string     | The manufacturer name for a `have_manufacturers` rule                                            |
| `data.price_list.id`        | int        | The price list id for an `in_price_list` rule                                                    |
| `data.price_list.name`      | string     | The price list name for an `in_price_list` rule                                                  |
| `data.category.id`          | int        | The category id for an `in_category` rule                                                        |
| `data.category.name`        | string     | The category name for an `in_category` rule                                                      |
| `data.days`                 | int        | The days for a `published_within_days` rule                                                      |
| `data.start_at`             | timestamp  | The start at date for a `published_within` rule                                                  |
| `data.end_at`               | timestamp  | The end at date for a `published_within` rule                                                    |
| `data.min_price`            | float      | The min price **including tax**, in whole units (e.g. pounds not pence) for `price_between` rule |
| `data.max_price`            | float      | The max price **including tax**, in whole units (e.g. pounds not pence) for `price_between` rule |
| `data.currency`             | string     | The currency code for `price_between` rule                                                       |

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
GET /api/categories/{id|name|breadcrumb}
```

```json
{
    "id": 1,
    "name": "Mens",
    "parent": null,
    "reference": null,
    "slug": "mens",
    "featured_image": {
        "url": null
    },
    "content": {
        "summary": "",
        "description": "",
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
    "tags": [],
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
        "heading": "",
        "page_title": "",
        "meta_description": "",
        "open_graph": "",
        "canonical": "",
        "noindex": null,
        "nofollow": null
    },
    "settings": [],
    "additional_attributes": []
}
```

[Back to contents](../../README.md#table-of-contents)
