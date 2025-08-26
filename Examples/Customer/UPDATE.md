# Update Customer

## Attributes:

### Customer
| Name                    | Type      | Description                                                                                  | Required? |
|-------------------------|-----------|----------------------------------------------------------------------------------------------|-----------|
| `name`                  | string    | The name of the customer                                                                     | No        |
| `email`                 | string    | The email of the customer                                                                    | No        |
| `group`                 | string    | The group name of the customer                                                               | No        |
| `tax_group`             | string    | The tax group name of the customer                                                           | No        |
| `additional_attributes` | array     | The additional attributes of the customer, see [Additional Attribute](#additional-attribute) | No        |

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
            "key": "api",
            "value": "true"
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
