# Store Collection

## Attributes:

### Collection

| Name                    | Type   | Description                                                                                    | Required? |
|-------------------------|--------|------------------------------------------------------------------------------------------------|-----------|
| `name`                  | string | The name of the collection                                                                     | Yes       |
| `slug`                  | string | The slug of the collection, if not present it is auto-generated from name                      | No        |
| `reference`             | string | The reference of the collection                                                                | No        |
| `logic`                 | string | The logic of the rules for the collection, and/or (defaults to or if not provided)             | No        |
| `published_at`          | date   | The published at of the collection                                                             | No        |
| `rules`                 | array  | The listing page rules of the collection, see [Rule](#rule)                                    | No        |
| `content`               | object | The listing page content of the collection, see [Content](#content)                            | No        |
| `options`               | object | The listing page options of the collection, see [Options](#options)                            | No        |
| `seo`                   | object | The SEO of the collection, see [SEO](#seo)                                                     | No        |
| `additional_attributes` | array  | The additional attributes of the collection, see [Additional Attribute](#additional-attribute) | No        |

### Image

| Name  | Type   | Description             | Required? |
|-------|--------|-------------------------|-----------|
| `src` | string | The source of the image | Yes       |

### Rule

| Name                 | Type   | Description                                                                                                                                           | Required?   |
|----------------------|--------|-------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| `type`               | string | The type of the rule, e.g. in_category, in_price_list, have_manufacturers, have_tags, price_between, reduced, published_within_days, published_within | Yes         |
| `requirement`        | string | The requirement of the rule, must/must_not (defaults to must if not provided)                                                                         | No          |
| `logic`              | string | The logic of the rule, and/or (defaults to or if not provided)                                                                                        | No          |
| `data`               | object | The data for the rule, required keys vary based on `type` of the rule                                                                                 | Yes         |
| `data.tags`          | array  | The tag ids (or names formatted as `group\|name`) for a `have_tags` rule                                                                              | Conditional |
| `data.manufacturers` | array  | The manufacturer ids (or names) for a `have_manufacturers` rule                                                                                       | Conditional |
| `data.price_list`    | int    | The price list id for an `in_price_list` rule                                                                                                         | Conditional |
| `data.category`      | int    | The category id for an `in_category` rule                                                                                                             | Conditional |
| `data.days`          | int    | The days for a `published_within_days` rule                                                                                                           | Conditional |
| `data.start_at`      | date   | The start at date for a `published_within` rule                                                                                                       | Conditional |
| `data.end_at`        | date   | The end at date for a `published_within` rule (optional)                                                                                              | Conditional |
| `data.min_price`     | float  | The min price **including tax**, in store's default currency & in whole units (e.g. pounds not pence) for `price_between` rule                        | Conditional |
| `data.max_price`     | float  | The max price **including tax**, in store's default currency & in whole units (e.g. pounds not pence) for `price_between` rule                        | Conditional |

**NOTE:** The `rules` are nested within arrays to achieve grouping, see Example payload for more clarity

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
        {
          "id": 1
        }
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

