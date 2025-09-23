# Store Category

## Overview

This endpoint creates a new category using the provided json data

## Structure

### Category

| Name                    | Type    | Description                                                                      | Required? |
|-------------------------|---------|----------------------------------------------------------------------------------|-----------|
| `id`                    | int     | The id for the category                                                          | No        |
| `name`                  | string  | The name of the category                                                         | Yes       |
| `parent`                | string  | The parent of the category                                                       | No        |
| `slug`                  | string  | The slug of the category, if not present it is auto-generated from name          | No        |
| `reference`             | string  | The reference of the category                                                    | No        |
| `logic`                 | string  | The logic of the rules for the category, and/or (defaults to or if not provided) | No        |
| `visible`               | boolean | The visibility of the category (defaults to `true`)                              | No        |
| `featured_image`        | object  | The [Image](#image) of the category                                              | No        |
| `tags`                  | array   | An array of [Tag](#tag) objects                                                  | No        |
| `rules`                 | array   | An array of Listing Page [Rule](#rule) objects                                   | No        |
| `content`               | object  | The Listing Page [Content](#content) of the category                             | No        |
| `options`               | object  | The Listing Page [Options](#options) of the category                             | No        |
| `seo`                   | object  | The [SEO](#seo) of the category                                                  | No        |
| `additional_attributes` | array   | An array of [Additional Attribute](#additional-attribute) objects                | No        |

### Image

| Name  | Type   | Description                 | Required? |
|-------|--------|-----------------------------|-----------|
| `src` | string | The source url of the image | Yes       |

### Tag

| Name       | Type   | Description                                | Required? |
|------------|--------|--------------------------------------------|-----------|
| `name`     | string | The name of the tag (e.g., Small or Red)   | Yes       |
| `group`    | object | The tag group, see [Tag Group](#tag-group) | Yes       |

### Tag Group

| Name      | Type   | Description                                      | Required? |
|-----------|--------|--------------------------------------------------|-----------|
| `name`    | string | The name of the tag group (e.g., Size or Colour) | Yes       |

### Rule

| Name                 | Type      | Description                                                                                                                                                           | Required?    |
|----------------------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| `type`               | string    | Rule type. Allowed values: `in_category`, `in_price_list`, `have_manufacturers`, `have_tags`, `price_between`, `reduced`, `published_within_days`, `published_within` | Yes          |
| `requirement`        | string    | Requirement for the rule. Allowed values: `must`, `must_not`. Defaults to `must`                                                                                      | No           |
| `logic`              | string    | How this rule combines with others. Allowed values: `and`, `or`. Defaults to `or`                                                                                     | No           |
| `data`               | object    | Rule-specific data (see below). Keys vary depending on type                                                                                                           | Yes          |
| `data.tags`          | array     | An array of Tag ids (or names formatted as group\|name). Required if `type = have_tags`                                                                               | Conditional  |
| `data.manufacturers` | array     | An array of manufacturer ids (or names). Required if `type = have_manufacturers`                                                                                      | Conditional  |
| `data.price_list`    | string    | Price list id (or name). Required if `type = in_price_list`                                                                                                           | Conditional  |
| `data.category`      | string    | Category id (or name/breadcrumb, e.g., Mens > Coats). Required if `type = in_category`                                                                                | Conditional  |
| `data.days`          | int       | Number of days. Required if `type = published_within_days`                                                                                                            | Conditional  |
| `data.start_at`      | timestamp | The start date. Required if `type = published_within`                                                                                                                 | Conditional  |
| `data.end_at`        | timestamp | The end date. Optional if `type = published_within`                                                                                                                   | Conditional  |
| `data.min_price`     | float     | Minimum price (including tax) in store’s default currency, whole units only (e.g. pounds, not pence). Required if `type = price_between`                              | Conditional  |
| `data.max_price`     | float     | Maximum price (including tax) in store’s default currency, whole units only. Required if `type = price_between`                                                       | Conditional  |

**NOTE:** The `rules` are nested within arrays to achieve grouping, see `rules` in [Example Request](#example-request) for clarity

### Content

| Name           | Type   | Description                | Required? |
|----------------|--------|----------------------------|-----------|
| `summary`      | string | The summary content        | No        |
| `description`  | string | The description content    | No        |
| `small_image`  | object | The Small [Image](#image)  | No        |
| `medium_image` | object | The Medium [Image](#image) | No        |
| `large_image`  | object | The Large [Image](#image)  | No        |

### Options

| Name                         | Type    | Description                                                                                                           | Required?    |
|------------------------------|---------|-----------------------------------------------------------------------------------------------------------------------|--------------|
| `categories.mode`            | string  | Categories filter display mode. Allowed values: `show_all`, `hide_all`, `show_some`. Default: `show_all`              | No           |
| `categories.values`          | array   | An array of category ids (or names/breadcrumbs, e.g. Mens > Coats) to show. Required if `categories.mode = show_some` | Conditional  |
| `filters.mode`               | int     | Facet filters display mode. Allowed values: `show_all`, `hide_all`, `show_some`. Default: `show_all`                  | No           |
| `filters.values`             | array   | The options for facet filters on the listings page. Required if `filters.mode = show_some`                            | Conditional  |
| `filters.values.*.name`      | string  | The name of the facet filter, e.g. `Category`, `Price`, etc...                                                        | Yes          |
| `filters.values.*.collapsed` | boolean | Whether to collapse the facet filter or not                                                                           | Yes          |
| `sort_bys`                   | array   | An array of the applied sorts on the listings page (e.g., name-az, name-za, price-low, price-high, etc...)            | No           |
| `per_page`                   | int     | The per page of the listings page (defaults to 24)                                                                    | No           |

### SEO

| Name               | Type      | Description                | Required? |
|--------------------|-----------|----------------------------|-----------|
| `heading`          | string    | The SEO Heading            | No        |
| `page_title`       | string    | The SEO Page Title         | No        |
| `meta_description` | string    | The SEO Meta Description   | No        |
| `canonical`        | string    | The SEO Canonical          | No        |
| `noindex`          | boolean   | The SEO No Index           | No        |
| `nofollow`         | boolean   | The SEO No Follow          | No        |

### Additional Attribute

| Name    | Type    | Description                           | Required? |
|---------|---------|---------------------------------------|-----------|
| `key`   | string  | The key of the additional attribute   | Yes       |
| `value` | string  | The value of the additional attribute | Yes       |

## Example Request

```http request
POST /api/categories/
```

```json lines
{
    "name": "Mens 2",
    "slug": "mens-2",
    "parent": 1,
    "visible": false,
    "content": {
        "summary": "Listing Page Summary Description",
        "description": "Listing Page Content Description"
    },
    "tags": [
        {
            "group": {
                "name": "Size"
            },
            "name": "Small"
        }
    ],
    "rules": [
        [
            {
                "type": "have_tags",
                "requirement": "must",
                "logic": "or",
                "data": {
                    "tags": [
                        1
                    ]
                }
            },
            {
                "type": "in_category",
                "requirement": "must",
                "logic": "and",
                "data": {
                    "category": 1
                }
            }
        ],
        [
            {
                "type": "in_price_list",
                "requirement": "must",
                "logic": "and",
                "data": {
                    "price_list": 1
                }
            }
        ],
        [
            {
                "type": "price_between",
                "requirement": "must",
                "logic": "and",
                "data": {
                    "min_price": 100,
                    "max_price": 200
                }
            },
            {
                "type": "reduced",
                "requirement": "must",
                "logic": "and"
            }
        ],
        [
            {
                "type": "published_within_days",
                "requirement": "must",
                "logic": "and",
                "data": {
                    "days": "12"
                }
            },
            {
                "type": "have_manufacturers",
                "requirement": "must",
                "logic": "and",
                "data": {
                    "manufacturers": [
                        1
                    ]
                }
            }
        ]
    ],
    "options": {
        "categories": {
            "mode": "show_some",
            "values": [
                1
            ]
        },
        "filters": {
            "mode": "show_some",
            "values": [
                {
                    "name": "Price",
                    "collapsed": true
                },
                {
                    "name": "Manufacturer"
                }
            ]
        },
        "sort_bys": [
            "model-az",
            "manufacturer-za"
        ],
        "per_page": 2
    },
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

## Example Response

```json
{
    "category": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
