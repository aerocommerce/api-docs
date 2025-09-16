# Order Index

## Overview

This endpoint retrieves a paginated list of all orders

## Structure

See [View Order](VIEW.md) for the structure of the order payloads inside the `data` array

## Remarks

This is a paginated route (see [Pagination Conventions](../../CONVENTIONS.md#pagination-conventions))

In addition to the standard parameters accepted for a paginated route, this route also accepts:

| Parameter        | Description                     | Example                                 |
|------------------|---------------------------------|-----------------------------------------|
| `min_ordered_at` | The min ordered at for an order | ?min_ordered_at=2023-08-30%2010:35:05   |
| `max_ordered_at` | The max ordered at for an order | ?max_ordered_at=2023-08-30%2010:35:05   |

see [Date Conventions](../../CONVENTIONS.md#date-conventions) for more info on acceptable values for these parameters

## Scopes

| Name      | Description                                                | Example        |
|-----------|------------------------------------------------------------|----------------|
| `visible` | Only return visible orders (those which have been ordered) | ?scope=visible |

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
