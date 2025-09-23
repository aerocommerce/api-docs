# Order Index

## Overview

This endpoint retrieves a paginated list of all orders

## Structure

See [View Order](VIEW.md) for the structure of the order payloads inside the `data` array

## Scopes

| Name           | Description                                                | Example            |
|----------------|------------------------------------------------------------|--------------------|
| `visible`      | Only return visible orders (those which have been ordered) | ?scope=visible     |
| `outstanding`  | Only return outstanding orders                             | ?scope=outstanding |
| `completed`    | Only return completed orders                               | ?scope=completed   |
| `incomplete`   | Only return incomplete orders                              | ?scope=incomplete  |
| `express`      | Only return express orders                                 | ?scope=express     |
| `standard`     | Only return standard orders                                | ?scope=standard    |

## Filters

| Name        | Description                                                 | Example                     |
|-------------|-------------------------------------------------------------|-----------------------------|
| `reference` | Only return orders with specific references                 | ?references=ABC123,DEF456   |
| `statuses`  | Only return orders with specific status ids or names        | ?statuses=1,On Hold         |
| `states`    | Only return orders with specific states                     | ?states=dispatched,returned |
| `customers` | Only return orders with specific customers (by id or email) | ?customers=1,test@gmail.com |
| `emails`    | Only return orders for specific emails                      | ?emails=test@gmail.com      |
| `channels`  | Only return orders for specific channels                    | ?channels=web,api           |

## Example Response

```http request
GET /api/orders?per_page=2&min_ordered_at=2023-08-30%2010:36:23
```

```json lines
{
    "current_page": 1,
    "data": [
      //...
    ],
    "first_page_url": "http://aero.test/api/orders?page=1",
    "from": 1,
    "last_page": 3,
    "last_page_url": "http://aero.test/api/orders?page=3",
    "next_page_url": "http://aero.test/api/orders?page=2",
    "path": "http://aero.test/api/orders",
    "per_page": 2,
    "prev_page_url": null,
    "to": 2,
    "total": 5
}
```

[Back to contents](../../README.md#table-of-contents)
