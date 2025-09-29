# Store Location

This endpoint creates a new location using the provided json data

## Structure

### Location

| Name                    | Type   | Description                                                                     | Required?   |
|-------------------------|--------|---------------------------------------------------------------------------------|-------------|
| `id`                    | int    | The id for the location                                                         | No          |
| `name`                  | string | The name of the location                                                        | Yes         |
| `email`                 | string | The email of the location                                                       | No          |
| `phone`                 | string | The phone number for the location                                               | No          |
| `line_1`                | string | The first line for the location                                                 | Yes         |
| `line_2`                | string | The second line for the location                                                | No          |
| `city`                  | string | The city for the location                                                       | Yes         |
| `county`                | string | The county for the location                                                     | No          |
| `zone`                  | string | The zone code for the location, required for some countries (e.g., US, AU, etc) | Conditional |
| `postcode`              | string | The postcode for the location, required for some countries (e.g., GB, US, etc)  | Conditional |
| `country`               | string | The country code for the location                                               | Yes         |
| `latitude`              | float  | The latitude for the location                                                   | No          |
| `longitude`             | float  | The longitude for the location                                                  | No          |
| `opening_hours`         | object | See [Opening Hours](#opening-hours)                                             | No          |
| `additional_attributes` | array  | An array of [Additional Attribute](#additional-attribute) objects               | No          |

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
POST /api/locations/
```

```json lines
{
    "name": "Aero Commerce",
    "line_1": "28-32 Albert Rd",
    "city": "Middlesbrough",
    "postcode": "TS1 1QD",
    "country": "GB",
    "opening_hours": {
        "monday": {
            "times": [
                {
                    "start": "07:00",
                    "end": "12:00"
                },
                {
                    "start": "12:30",
                    "end": "15:00"
                }
            ]
        },
        "tuesday": {
            "times": [
                {
                    "start": "07:00",
                    "end": "12:00"
                },
                {
                    "start": "12:30",
                    "end": "15:00"
                }
            ]
        },
        "wednesday": {
            "times": [
                {
                    "start": "07:00",
                    "end": "12:00"
                },
                {
                    "start": "12:30",
                    "end": "15:00"
                }
            ]
        },
        "thursday": {
            "times": [
                {
                    "start": "07:00",
                    "end": "12:00"
                },
                {
                    "start": "12:30",
                    "end": "15:00"
                }
            ]
        },
        "friday": {
            "times": [
                {
                    "start": "07:00",
                    "end": "12:00"
                },
                {
                    "start": "12:30",
                    "end": "15:00"
                }
            ]
        },
        "overrides": [
            {
                "date": "2025-12-25",
                "label": "Christmas Day"
            },
            {
                "date": "2025-08-25",
                "label": "Bank Holiday"
            }
        ]
    }
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
