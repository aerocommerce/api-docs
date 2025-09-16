# Update Customer

## Overview

This endpoint updates an existing customer by its `id`. Only the fields provided in the request will be updated; unspecified fields remain unchanged.

## Structure

### Customer
| Name                    | Type      | Description                                                       | Required? |
|-------------------------|-----------|-------------------------------------------------------------------|-----------|
| `name`                  | string    | The name of the customer                                          | No        |
| `email`                 | string    | The email of the customer                                         | No        |
| `group`                 | string    | The group name of the customer                                    | No        |
| `tax_group`             | string    | The tax group name of the customer                                | No        |
| `additional_attributes` | array     | An array of [Additional Attribute](#additional-attribute) objects | No        |

### Additional Attribute

| Name    | Type    | Description                           | Required? |
|---------|---------|---------------------------------------|-----------|
| `key`   | string  | The key of the additional attribute   | Yes       |
| `value` | string  | The value of the additional attribute | Yes       |

## Example Request

```http request
PUT /api/customers/{id}
```

```json lines
{
    "name": "Test",
    "email": "test@gmail.com",
    "group": "Group Name",
    "additional_attributes": [
        {
            "key": "last-api-update",
            "value": "2023-09-01 09:29:41"
        }
    ]
}
```

## Example Response

```json
{
    "customer": {
        "id": 1
    }
}
```

[Back to contents](../../README.md#table-of-contents)
