# View Manufacturer

## Attributes:

### Manufacturer

| Name                    | Type   | Description                                                                                        | 
|-------------------------|--------|----------------------------------------------------------------------------------------------------|
| `name`                  | string | The name of the manufacturer                                                                       |
| `slug`                  | string | The slug of the manufacturer                                                                       |
| `reference`             | string | The reference of the manufacturer                                                                  |
| `logic`                 | string | The logic of the rules for the manufacturer                                                        |
| `logo`                  | object | The logo of the manufacturer, see [Image](#image)                                                  |
| `tags`                  | array  | The tags of the manufacturer, see [Tag](#tag)                                                      |
| `related_manufacturers` | array  | The related manufacturers of the manufacturer, see [Related Manufacturers](#related-manufacturers) |
| `rules`                 | array  | The listing page rules of the manufacturer, see [Rule](#rule)                                      |
| `content`               | object | The listing page content of the manufacturer, see [Content](#content)                              |
| `options`               | object | The listing page options of the manufacturer, see [Options](#options)                              |
| `seo`                   | object | The SEO of the manufacturer, see [SEO](#seo)                                                       |
| `additional_attributes` | array  | The additional attributes of the manufacturer, see [Additional Attribute](#additional-attribute)   |

### Image

| Name  | Type   | Description             |
|-------|--------|-------------------------|
| `url` | string | The source of the image |

### Tag

| Name       | Type   | Description                                |
|------------|--------|--------------------------------------------|
| `name`     | string | The name of the tag                        |
| `group`    | object | The tag group, see [Tag Group](#tag-group) |

### Tag Group

| Name      | Type   | Description               |
|-----------|--------|---------------------------|
| `name`    | string | The name of the tag group |

### Related Manufacturers

| Name   | Type  | Description                  |
|--------|-------|------------------------------|
| `id`   | int   | The id of the manufacturer   |
| `name` | sting | The name of the manufacturer |

### Rule

| Name                 | Type   | Description                                                                                      |
|----------------------|--------|--------------------------------------------------------------------------------------------------|
| `type`               | string | The type of the rule                                                                             |
| `requirement`        | string | The requirement of the rule                                                                      |
| `logic`              | string | The logic of the rule                                                                            |
| `data`               | object | The data for the rule, required keys vary based on `type` of the rule                            |
| `data.tags`          | array  | The tag ids for a `have_tags` rule                                                               |
| `data.manufacturers` | array  | The manufacturer ids for a `have_manufacturers` rule                                             |
| `data.price_list`    | int    | The price list id for an `in_price_list` rule                                                    |
| `data.category`      | int    | The category id for an `in_category` rule                                                        |
| `data.days`          | int    | The days for a `published_within_days` rule                                                      |
| `data.start_at`      | date   | The start at date for a `published_within` rule                                                  |
| `data.end_at`        | date   | The end at date for a `published_within` rule                                                    |
| `data.min_price`     | float  | The min price **including tax**, in whole units (e.g. pounds not pence) for `price_between` rule |
| `data.max_price`     | float  | The max price **including tax**, in whole units (e.g. pounds not pence) for `price_between` rule |
| `data.currency`      | string | The currency code for `price_between` rule                                                       |

### Content

| Name           | Type   | Description                           | Required? |
|----------------|--------|---------------------------------------|-----------|
| `summary`      | string | The summary content                   | No        |
| `description`  | string | The description content               | No        |
| `small_image`  | object | The small image, see [Image](#image)  | No        |
| `medium_image` | object | The medium image, see [Image](#image) | No        |
| `large_image`  | object | The large image, see [Image](#image)  | No        |

### Options

| Name                         | Type    | Description                                                                                   | Required?   |
|------------------------------|---------|-----------------------------------------------------------------------------------------------|-------------|
| `categories.mode`            | string  | The categories mode, e.g. show_all/hide_all/show_some (defaults to show_all)                  | No          |
| `categories.values`          | array   | The options for categories on the listings page (required if and only if mode is `show_some`) | No          |
| `categories.values.*.id`     | int     | The id of category to show (required if and only if mode is `show_some`)                      | Conditional |
| `filters.mode`               | int     | The filters mode, e.g. show_all/hide_all/show_some (defaults to show_all)                     | No          |
| `filters.values`             | array   | The options for filters on the listings page (required if and only if mode is `show_some`)    | Conditional |
| `filters.values.*.name`      | string  | The name of the filter, e.g. Manufacturer, Price, etc...                                      | Yes         |
| `filters.values.*.collapsed` | boolean | Whether to collapse the filter or not                                                         | Yes         |
| `sort_bys`                   | array   | The applied sort bys on the listings page                                                     | No          |
| `sort_bys.*`                 | string  | The applied sort by, e.g. name-az, name-za, price-low, price-high, etc...                     | No          |
| `per_page`                   | int     | The per page of the listings page (defaults to 24)                                            | No          |

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
