# API Conventions

## Payload Conventions

Here are the main conventions & exceptions to those conventions that our payloads abide by, any more specific exceptions will be addressed in the relevant section in `Payloads`

### Attribute Conventions

When passing attribute data to the API the key will typically match the attribute name on the respective model, the one main exception to this are any attribute ending with '_code' will lose its suffix (e.g.: 'currency_code' => 'currency')

### Relationship Conventions

When passing nested (related) data to the API the key should be a snake case representation of the relationship method between the model and related model, e.g.: `shippingMethod` => `shipping_method`

### Price Conventions

All requests expect amounts to be provided in the currency's smallest unit. For example, to charge 10 GBP, provide an amount value of 1000 (that is, 1000 pence).

When passing a price it should be formatted as a nested json object with `amount` & `tax` keys where the `amount` is the price **excluding tax**, e.g.:

```json lines
{
    "price": {
        "amount": 40000, // Excluding tax
        "tax": 8000
    }
}
```

### Date Conventions

When passing a date it must be Carbon parseable, e.g.: `"2023-09-01T09:29:41.000000Z"` or `"2023-09-01 09:29:41"` or `"2023-09-01"`, if no time is provided midnight will be used as the date's time

[Back to contents](README.md#table-of-contents)
