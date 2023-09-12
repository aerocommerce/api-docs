# View Order Status

## Attributes

| Name               | Type   | Description                   |
|--------------------|--------|-------------------------------|
| `id`               | int    | The id of the order status    |
| `name`             | string | The name of the order status  |
| `state`            | string | The state of the order status |

## Remarks

The `state` is restricted to one of the following values:
- cancelled
- on_hold
- successful
- complete
- processing
- closed
- partially_dispatched
- dispatched
- partially_returned
- returned

[Back to contents](../../README.md#table-of-contents)
