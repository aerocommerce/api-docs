# View Location

## Overview

This endpoint retrieves a single location by `id` or `name`

## Structure

### Location

| Name                    | Type   | Description                                                                     |
|-------------------------|--------|---------------------------------------------------------------------------------|
| `id`                    | int    | The id for the location                                                         |
| `name`                  | string | The name of the location                                                        |
| `email`                 | string | The email of the location                                                       |
| `phone`                 | string | The phone number for the location                                               |
| `line_1`                | string | The first line for the location                                                 |
| `line_2`                | string | The second line for the location                                                |
| `city`                  | string | The city for the location                                                       |
| `county`                | string | The county for the location                                                     |
| `zone`                  | string | The zone code for the location, required for some countries (e.g., US, AU, etc) |
| `postcode`              | string | The postcode for the location, required for some countries (e.g., GB, US, etc)  |
| `country`               | string | The country code for the location                                               |
| `latitude`              | float  | The latitude for the location                                                   |
| `longitude`             | float  | The longitude for the location                                                  |
| `opening_hours`         | object | See [Opening Hours](#opening-hours)                                             |
| `additional_attributes` | array  | An array of [Additional Attribute](#additional-attribute) objects               |

### Opening Hours

| Name              | Type   | Description                       |
|-------------------|--------|-----------------------------------|
| `sunday.times`    | array  | An array of [Time](#time) objects |
| `monday.times`    | array  | An array of [Time](#time) objects |
| `tuesday.times`   | array  | An array of [Time](#time) objects |
| `wednesday.times` | array  | An array of [Time](#time) objects |
| `thursday.times`  | array  | An array of [Time](#time) objects |
| `friday.times`    | array  | An array of [Time](#time) objects |
| `saturday.times`  | array  | An array of [Time](#time) objects |
| `overrides`       | object | See [Overrides](#overrides)       |

### Time

| Name    | Type   | Description                 |
|---------|--------|-----------------------------|
| `start` | time   | The start of the time range |
| `end`   | time   | The end of the time range   |

### Overrides

| Name    | Type   | Description                       |
|---------|--------|-----------------------------------|
| `date`  | date   | The date the override is for      |
| `label` | string | The label for the override        |
| `times` | array  | An array of [Time](#time) objects |

### Additional Attribute

| Name    | Type    | Description                           |
|---------|---------|---------------------------------------|
| `key`   | string  | The key of the additional attribute   |
| `value` | string  | The value of the additional attribute |

## Example Response

```http request
GET /api/locations/{id|name}
```

```json
{
    "id": 1,
    "name": "Aero Commerce",
    "email": null,
    "phone": null,
    "latitude": null,
    "longitude": null,
    "line_1": "28-32 Albert Rd",
    "line_2": null,
    "city": "Middlesbrough",
    "county": null,
    "zone": null,
    "postcode": "TS1 1QD",
    "country": "GB",
    "opening_hours": {
        "sunday": {
            "times": []
        },
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
        "saturday": {
            "times": []
        },
        "overrides": [
            {
                "date": "2025-12-25",
                "label": "Christmas Day",
                "times": []
            },
            {
                "date": "2025-08-25",
                "label": "Bank Holiday",
                "times": []
            }
        ]
    },
    "additional_attributes": []
}
```

[Back to contents](../../README.md#table-of-contents)
