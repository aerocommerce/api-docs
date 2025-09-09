# Update Manufacturer

## Attributes:

### Manufacturer

| Name                    | Type   | Description                                                                                      | Required? |
|-------------------------|--------|--------------------------------------------------------------------------------------------------|-----------|
| `name`                  | string | The name of the manufacturer                                                                     | No        |
| `slug`                  | string | The slug of the manufacturer                                                                     | No        |
| `reference`             | string | The reference of the manufacturer                                                                | No        |
| `logic`                 | string | The logic of the rules for the manufacturer: and/or                                              | No        |
| `logo`                  | object | The logo of the manufacturer, see [Image](#image)                                                | No        |
| `tags`                  | array  | The tags of the manufacturer, see [Tag](#tag)                                                    | No        |
| `related_manufacturers` | array  | An array of related manufacturers (ids and/or names)                                             | No        |
| `content`               | object | The listing page content of the manufacturer, see [Content](#content)                            | No        |
| `options`               | object | The listing page options of the manufacturer, see [Options](#options)                            | No        |
| `seo`                   | object | The SEO of the manufacturer, see [SEO](#seo)                                                     | No        |
| `additional_attributes` | array  | The additional attributes of the manufacturer, see [Additional Attribute](#additional-attribute) | No        |

### Image

| Name  | Type   | Description             | Required? |
|-------|--------|-------------------------|-----------|
| `src` | string | The source of the image | Yes       |

### Tag

| Name       | Type   | Description                                | Required? |
|------------|--------|--------------------------------------------|-----------|
| `name`     | string | The name of the tag                        | Yes       |
| `group`    | object | The tag group, see [Tag Group](#tag-group) | Yes       |

### Tag Group

| Name      | Type   | Description               | Required? |
|-----------|--------|---------------------------|-----------|
| `name`    | string | The name of the tag group | Yes       |

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
PUT /api/manufacturers/{id}
```

```json lines
{
    "name": "Updated Burberry",
    "slug": "very-burberry",
    "content": {
        "description": "Updated Burberry"
    },
    "seo": {
        "heading": "Updated Burberry"
    },
    "tags": [
        {
            "name": "Green",
            "group": {
                "name": "Colour"
            }
        }
    ]
}
```

## Example Response

```json
{
    "manufacturer": {
        "id": 1
    }
}
```

