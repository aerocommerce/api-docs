# View Manufacturer

## Overview

This endpoint retrieves a single manufacturer by `id` or `name`

## Structure

### Manufacturer

| Name                     | Type    | Description                                                                                        | 
|--------------------------|---------|----------------------------------------------------------------------------------------------------|
| `name`                   | string  | The name of the manufacturer                                                                       |
| `slug`                   | string  | The slug of the manufacturer                                                                       |
| `reference`              | string  | The reference of the manufacturer                                                                  |
| `logic`                  | string  | The logic of the rules for the manufacturer                                                        |
| `logo`                   | object  | The logo of the manufacturer, see [Image](#image)                                                  |
| `tags`                   | array   | An array of [Tag](#tag) objects                                                                    |
| `related_manufacturers`  | array   | The related manufacturers of the manufacturer, see [Related Manufacturers](#related-manufacturers) |
| `rules`                  | array   | An array of Listing Page [Rule](#rule) objects                                                     |
| `content`                | object  | The Listing Page [Content](#content) of the category                                               |
| `options`                | object  | The Listing Page [Options](#options) of the category                                               |
| `seo`                    | object  | The [SEO](#seo) of the category                                                                    |
| `additional_attributes`  | array   | An array of [Additional Attribute](#additional-attribute) objects                                  |

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

### Related Manufacturers

| Name   | Type  | Description                  |
|--------|-------|------------------------------|
| `id`   | int   | The id of the manufacturer   |
| `name` | sting | The name of the manufacturer |

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
GET /api/manufacturers/{id}
```

```json
{
    "id": 1,
    "name": "Burberry",
    "reference": null,
    "slug": "burberry",
    "logo": {
        "url": null
    },
    "content": {
        "summary": "Listing Page Summary Description",
        "description": "Listing Page Content Description",
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
    "related_manufacturers": [
        {
            "id": 8,
            "name": "Aztech Mountain"
        }
    ],
    "rules": [],
    "options": {
        "categories": {
            "mode": "show_some",
            "values": [
                {
                    "id": 2,
                    "name": "Coats"
                }
            ]
        },
        "filters": {
            "mode": "show_some",
            "values": [
                {
                    "key": "t2",
                    "name": "Colour",
                    "collapsed": true
                },
                {
                    "key": "t1",
                    "name": "Size",
                    "collapsed": false
                },
                {
                    "key": "p",
                    "name": "Price",
                    "collapsed": false
                },
                {
                    "key": "m",
                    "name": "Manufacturer",
                    "collapsed": false
                },
                {
                    "key": "c",
                    "name": "Category",
                    "collapsed": false
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
    "settings": [],
    "additional_attributes": [
        {
            "key": "test_name",
            "value": "test_value"
        }
    ]
}
```

[Back to contents](../../README.md#table-of-contents)
