# Update Manufacturer

## Overview

This endpoint updates an existing category by its `id` or `name`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Manufacturer

| Name                    | Type   | Description                                                                         | Required? |
|-------------------------|--------|-------------------------------------------------------------------------------------|-----------|
| `name`                  | string | The name of the manufacturer                                                        | No        |
| `slug`                  | string | The slug of the manufacturer                                                        | No        |
| `reference`             | string | The reference of the manufacturer                                                   | No        |
| `logic`                 | string | The logic of the rules for the manufacturer: and/or                                 | No        |
| `logo`                  | object | The logo of the manufacturer, see [Image](#image)                                   | No        |
| `tags`                  | array  | An array of [Tag](#tag) objects                                                     | No        |
| `related_manufacturers` | array  | An array of related manufacturers (ids and/or names)                                | No        |
| `rules`                 | array  | An array of Listing Page [Rule](#rule) objects                                      | No        |
| `content`               | object | The Listing Page [Content](#content) of the category                                | No        |
| `options`               | object | The Listing Page [Options](#options) of the category                                | No        |
| `seo`                   | object | The [SEO](#seo) of the category                                                     | No        |
| `additional_attributes` | array  | An array of [Additional Attribute](#additional-attribute) objects                   | No        |

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
PUT /api/manufacturers/{id|name}
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

[Back to contents](../../README.md#table-of-contents)
