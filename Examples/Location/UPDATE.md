# Update Location

This endpoint updates an existing location  by its `id` or `name`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Location

| Name                    | Type   | Description                                                                     | Required? |
|-------------------------|--------|---------------------------------------------------------------------------------|-----------|
| `id`                    | int    | The id for the location                                                         | No        |
| `name`                  | string | The name of the location                                                        | No        |
| `email`                 | string | The email of the location                                                       | No        |
| `phone`                 | string | The phone number for the location                                               | No        |
| `line_1`                | string | The first line for the location                                                 | No        |
| `line_2`                | string | The second line for the location                                                | No        |
| `city`                  | string | The city for the location                                                       | No        |
| `county`                | string | The county for the location                                                     | No        |
| `zone`                  | string | The zone code for the location, required for some countries (e.g., US, AU, etc) | No        |
| `postcode`              | string | The postcode for the location, required for some countries (e.g., GB, US, etc)  | No        |
| `country`               | string | The country code for the location                                               | No        |
| `latitude`              | float  | The latitude for the location                                                   | No        |
| `longitude`             | float  | The longitude for the location                                                  | No        |
| `opening_hours`         | object | See [Opening Hours](#opening-hours)                                             | No        |
| `additional_attributes` | array  | An array of [Additional Attribute](#additional-attribute) objects               | No        |

### Opening Hours

| Name              | Type   | Description                       | Required? |
|-------------------|--------|-----------------------------------|-----------|
| `sunday.times`    | array  | An array of [Time](#time) objects | No        |
| `monday.times`    | array  | An array of [Time](#time) objects | No        |
| `tuesday.times`   | array  | An array of [Time](#time) objects | No        |
| `wednesday.times` | array  | An array of [Time](#time) objects | No        |
| `thursday.times`  | array  | An array of [Time](#time) objects | No        |
| `friday.times`    | array  | An array of [Time](#time) objects | No        |
| `saturday.times`  | array  | An array of [Time](#time) objects | No        |
| `overrides`       | object | See [Overrides](#overrides)       | No        |

### Time

| Name    | Type   | Description                 | Required? |
|---------|--------|-----------------------------|-----------|
| `start` | time   | The start of the time range | Yes       |
| `end`   | time   | The end of the time range   | Yes       |

### Overrides

| Name    | Type   | Description                       | Required? |
|---------|--------|-----------------------------------|-----------|
| `date`  | date   | The date the override is for      | Yes       |
| `label` | string | The label for the override        | No        |
| `times` | array  | An array of [Time](#time) objects | No        |

### Additional Attribute

| Name    | Type    | Description                           | Required? |
|---------|---------|---------------------------------------|-----------|
| `key`   | string  | The key of the additional attribute   | Yes       |
| `value` | string  | The value of the additional attribute | Yes       |

## Example Request

```http request
PUT /api/locations/{id|name}
```

```json lines
{
    "opening_hours": {
        "monday": {
            "times": [
                {
                    "start": "09:00",
                    "end": "12:30"
                },
                {
                    "start": "13:00",
                    "end": "17:00"
                }
            ]
        },
        "overrides": [
            {
                "date": "2025-12-25",
                "label": "Christmas Day",
                "times": []
            }
        ]
    },
}
```

## Example Response

```json
{
    "location": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
