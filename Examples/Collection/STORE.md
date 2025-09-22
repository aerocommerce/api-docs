# Store Collection

## Overview

This endpoint creates a new collection using the provided json data

## Structure

### Collection

| Name                    | Type      | Description                                                                        | Required? |
|-------------------------|-----------|------------------------------------------------------------------------------------|-----------|
| `name`                  | string    | The name of the collection                                                         | Yes       |
| `slug`                  | string    | The slug of the collection, if not present it is auto-generated from name          | No        |
| `reference`             | string    | The reference of the collection                                                    | No        |
| `logic`                 | string    | The logic of the rules for the collection, and/or (defaults to or if not provided) | No        |
| `published_at`          | timestamp | The published at of the collection                                                 | No        |
| `rules`                 | array     | An array of Listing Page [Rule](#rule) objects                                     | No        |
| `content`               | object    | The Listing Page [Content](#content) of the category                               | No        |
| `options`               | object    | The Listing Page [Options](#options) of the category                               | No        |
| `seo`                   | object    | The [SEO](#seo) of the category                                                    | No        |
| `additional_attributes` | array     | An array of [Additional Attribute](#additional-attribute) objects                  | No        |

### Image

| Name  | Type   | Description                 | Required? |
|-------|--------|-----------------------------|-----------|
| `src` | string | The source url of the image | Yes       |

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
POST /api/collections/
```

```json lines
{
  "name": "Sale 2",
  "slug": "sale-2",
  "content": {
    "summary": "Listing Page Summary Description",
    "description": "Listing Page Content Description"
  },
  "rules": [
    [
      {
        "type": "have_tags",
        "requirement": "must",
        "logic": "or",
        "data": {
          "tags": [
            "size|small"
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
        "type": "have_manufacturers",
        "requirement": "must",
        "logic": "and",
        "data": {
          "manufacturers": [
            "Burberry"
          ]
        }
      },
      {
        "type": "published_within",
        "requirement": "must",
        "logic": "and",
        "data": {
          "start_at": "2025-09-03T06:52:00.000000Z",
          "end_at": "2025-09-20T06:52:00.000000Z"
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
    "page_title": "",
    "meta_description": "",
    "open_graph": "",
    "canonical": "",
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
    "collection": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
