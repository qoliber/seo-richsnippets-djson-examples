# ShippingDeliveryTime

An empty placeholder for your handling and transit times.

| | |
|---|---|
| Identifier | `shipping-delivery-time` |
| schema.org type | [ShippingDeliveryTime](https://schema.org/ShippingDeliveryTime) |
| Shown on by default | nowhere on its own: meant to be included |
| Includes | — |
| Included by | — |
| After install | inactive |

## What it publishes

Ships as `{}`, so it renders nothing, and no other template includes it. Fill it in when you want to publish delivery times, for example:

```json
{
    "@type": "ShippingDeliveryTime",
    "handlingTime": { "@type": "QuantitativeValue", "minValue": 0, "maxValue": 1, "unitCode": "DAY" },
    "transitTime": { "@type": "QuantitativeValue", "minValue": 1, "maxValue": 5, "unitCode": "DAY" }
}
```

Since the shipping details come from configuration as one object, the simplest way to publish this is a hand-written offer like **offer-shipping-details**, with `"deliveryTime": "{{snippet.shipping-delivery-time}}"` inside its `shippingDetails`.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{}
```

## Good to know

- Not rendered in the examples: an empty template produces no output.
