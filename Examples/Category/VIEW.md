# View Category

## Attributes:

### Category

| Name                    | Type    | Description                                                                                  | 
|-------------------------|---------|----------------------------------------------------------------------------------------------|
| `name`                  | string  | The name of the category                                                                     |
| `parent`                | string  | The parent of the category                                                                   |
| `slug`                  | string  | The slug of the category                                                                     |
| `reference`             | string  | The reference of the category                                                                |
| `visible`               | boolean | The visibility of the category                                                               |
| `logic`                 | string  | The logic of the rules for the category                                                      |
| `featured_image`        | object  | The featured image of the category, see [Image](#image)                                      |
| `tags`                  | array   | The tags of the category, see [Tag](#tag)                                                    |
| `rules`                 | array   | The listing page rules of the category, see [Rule](#rule)                                    |
| `content`               | object  | The listing page content of the category, see [Content](#content)                            |
| `options`               | object  | The listing page options of the category, see [Options](#options)                            |
| `seo`                   | object  | The SEO of the category, see [SEO](#seo)                                                     |
| `additional_attributes` | array   | The additional attributes of the category, see [Additional Attribute](#additional-attribute) |

### Image

| Name  | Type   | Description          |
|-------|--------|----------------------|
| `url` | string | The url of the image |

### Tag

| Name       | Type   | Description                                |
|------------|--------|--------------------------------------------|
| `name`     | string | The name of the tag                        |
| `group`    | object | The tag group, see [Tag Group](#tag-group) |

### Tag Group

| Name      | Type   | Description               |
|-----------|--------|---------------------------|
| `name`    | string | The name of the tag group |

### Rule

| Name                        | Type   | Description                                                                                      |
|-----------------------------|--------|--------------------------------------------------------------------------------------------------|
| `type`                      | string | The type of the rule                                                                             |
| `requirement`               | string | The requirement of the rule                                                                      |
| `logic`                     | string | The logic of the rule                                                                            |
| `data`                      | object | The data for the rule, required keys vary based on `type` of the rule                            |
| `data.tags`                 | array  | The tags for a `have_tags` rule, see [Tag](#tag)                                                 |
| `data.manufacturers.*.id`   | int    | The manufacturer id for a `have_manufacturers` rule                                              |
| `data.manufacturers.*.name` | string | The manufacturer name for a `have_manufacturers` rule                                            |
| `data.price_list.id`        | int    | The price list id for an `in_price_list` rule                                                    |
| `data.price_list.name`      | string | The price list name for an `in_price_list` rule                                                  |
| `data.category.id`          | int    | The category id for an `in_category` rule                                                        |
| `data.category.name`        | string | The category name for an `in_category` rule                                                      |
| `data.days`                 | int    | The days for a `published_within_days` rule                                                      |
| `data.start_at`             | date   | The start at date for a `published_within` rule                                                  |
| `data.end_at`               | date   | The end at date for a `published_within` rule                                                    |
| `data.min_price`            | float  | The min price **including tax**, in whole units (e.g. pounds not pence) for `price_between` rule |
| `data.max_price`            | float  | The max price **including tax**, in whole units (e.g. pounds not pence) for `price_between` rule |
| `data.currency`             | string | The currency code for `price_between` rule                                                       |

### Content

| Name           | Type   | Description                           |
|----------------|--------|---------------------------------------|
| `summary`      | string | The summary content                   |
| `description`  | string | The description content               |
| `small_image`  | object | The small image, see [Image](#image)  |
| `medium_image` | object | The medium image, see [Image](#image) |
| `large_image`  | object | The large image, see [Image](#image)  |

### Options

| Name                          | Type     | Description                                                                |
|-------------------------------|----------|----------------------------------------------------------------------------|
| `categories.mode`             | string   | The categories mode, e.g. show\_all/hide\_all/show\_some                   |
| `categories.values`           | array    | The options for categories on the listings page                            |
| `categories.values.*.id`      | int      | The id of category                                                         |
| `categories.values.*.name`    | string   | The name of category                                                       |
| `filters.mode`                | int      | The filters mode, e.g. show\_all/hide\_all/show\_some                      |
| `filters.values`              | array    | The options for filters on the listings page                               |
| `filters.values.*.name`       | string   | The name of the filter, e.g. Manufacturer, Price, etc...                   |
| `filters.values.*.collapsed`  | boolean  | Whether to collapse the filter or not                                      |
| `sort_bys`                    | array    | The applied sort bys on the listings page                                  |
| `sort_bys.*`                  | string   | The applied sort by, e.g. name-az, name-za, price-low, price-high, etc...  |
| `per_page`                    | int      | The per page of the listings page                                          |

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
GET /api/categories/{id}
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
