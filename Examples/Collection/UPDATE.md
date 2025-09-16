# Update Collection

## Overview

This endpoint updates an existing collection by its `id` or `name`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Collection

| Name                    | Type   | Description                                                                                    | Required? |
|-------------------------|--------|------------------------------------------------------------------------------------------------|-----------|
| `name`                  | string | The name of the collection                                                                     | No        |
| `slug`                  | string | The slug of the collection                                                                     | No        |
| `reference`             | string | The reference of the collection                                                                | No        |
| `logic`                 | string | The logic of the rules for the collection: and/or                                              | No        |
| `content`               | object | The listing page content of the collection, see [Content](#content)                            | No        |
| `options`               | object | The listing page options of the collection, see [Options](#options)                            | No        |
| `seo`                   | object | The SEO of the collection, see [SEO](#seo)                                                     | No        |
| `additional_attributes` | array  | The additional attributes of the collection, see [Additional Attribute](#additional-attribute) | No        |

### Image

| Name  | Type   | Description                 | Required? |
|-------|--------|-----------------------------|-----------|
| `src` | string | The source url of the image | Yes       |

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
PUT /api/collections/{id|name}
```

```json lines
{
    "name": "Updated Sale",
    "slug": "big-sale",
    "content": {
        "description": "Updated Sale"
    },
    "seo": {
        "heading": "Updated Sale"
    }
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

