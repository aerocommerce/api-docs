# Product Search

## Overview

This endpoint retrieves a paginated list of all products subject to scopes and filters via elastic-search

## Pre-requisites

This endpoint performs product search queries using Elasticsearch. Make sure your product documents are indexed before using this route:

```
php artisan aero:search:reindex --type=product
```

**NOTE:** You must run this command after installing the API on your store

## Structure

See [View Product](VIEW.md) for the structure of the product payloads inside the `data` array

## Scopes

| Name                 | Description                                     | Example                   |
|----------------------|-------------------------------------------------|---------------------------|
| `active`             | Only return active products                     | ?scope=active             |
| `inactive`           | Only return inactive products                   | ?scope=inactive           |
| `visible`            | Only return visible products                    | ?scope=visible            |
| `hidden`             | Only return hidden products                     | ?scope=hidden             |
| `categorised`        | Only return products that are in a category     | ?scope=categorised        |
| `un-categorised`     | Only return products that aren't in a category  | ?scope=un-categorised     |
| `published`          | Only return published products                  | ?scope=published          |
| `unpublished`        | Only return unpublished products                | ?scope=unpublished        |
| `scheduled`          | Only return scheduled to be published products  | ?scope=scheduled          |
| `has-stock`          | Only return products that have stock            | ?scope=has-stock          |
| `out-of-stock`       | Only return products that don't have stock      | ?scope=out-of-stock       |
| `not-tracking-stock` | Only return products that aren't tracking stock | ?scope=not-tracking-stock |
| `reduced`            | Only return reduced products                    | ?scope=reduced            |
| `not-reduced`        | Only return non-reduced products                | ?scope=not-reduced        |
| `has-images`         | Only return products that have images           | ?scope=has-images         |
| `no-images`          | Only return products that don't have images     | ?scope=no-images          |

## Filters

| Name              | Description                                                                             | Example                                                             |
|-------------------|-----------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| `manufacturers`   | Only return products with specific manufacturer ids (or names)                          | <span style="white-space: nowrap;">?manufacturers=1,burberry</span> |
| `tags`            | Only return products with specific tag ids (or names formatted as `group\|name`)        | <span style="white-space: nowrap;">?tags=1,colour\|red</span>       |
| `barcodes`        | Only return products with specific barcodes                                             | <span style="white-space: nowrap;">?barcodes=123,abc</span>         |
| `references`      | Only return products with specific references                                           | <span style="white-space: nowrap;">?references=123,abc</span>       |
| `price`           | Only return products with specific price in whole units (e.g. pounds, not pence)        | ?price=123                                                          |
| `min_price`       | Only return products with price above min price in whole units (e.g. pounds, not pence) | ?min_price=123                                                      |
| `max_price`       | Only return products with price below max price in whole units (e.g. pounds, not pence) | ?max_price=123                                                      |
| `stock_level`     | Only return products with specific stock level                                          | ?stock_level=1                                                      |
| `min_stock_level` | Only return products with stock above specific stock level                              | ?min_stock_level=1                                                  |
| `max_stock_level` | Only return products with stock below specific stock level                              | ?max_stock_level=10                                                 |
| `type`            | Only return products of a certain type (e.g. simple or variant)                         | ?type=variant                                                       |

**Note:** The `tags` filter applies AND logic across groups and OR logic within groups.  
- Example 1: `?tags=size|small,colour|red` = small AND red  
- Example 2: `?tags=colour|red,colour|green` = red OR green

**NOTE:** Plural filters can also be used in singular form, e.g. `?manufacturer=burberry` for `?manufacturers=burberry`

## Example Response

```http request
GET /api/products/search?per_page=2&min_updated_at=2023-08-30%2010:36:23&min_stock_level=1&max_stock_level=10
```

```json lines
{
    "current_page": 1,
    "data": [
        //...
    ],
    "first_page_url": "http://aero.test/api/products?page=1",
    "from": 1,
    "last_page": 16,
    "last_page_url": "http://aero.test/api/products?page=16",
    "next_page_url": "http://aero.test/api/products?page=2",
    "path": "http://aero.test/api/products",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 32
}
```

[Back to contents](../../README.md#table-of-contents)
