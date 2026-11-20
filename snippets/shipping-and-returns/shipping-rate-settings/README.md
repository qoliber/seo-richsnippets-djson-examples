# ShippingRateSettings

The same configured shipping policy as shipping-details, under the name offer-shipping-details uses.

| | |
|---|---|
| Identifier | `shipping-rate-settings` |
| schema.org type | [OfferShippingDetails](https://schema.org/OfferShippingDetails) |
| Shown on by default | nowhere on its own: included by other templates |
| Includes | — |
| Included by | [`offer-shipping-details`](../../product-pages/offer-shipping-details/) |
| After install | inactive |

## What it publishes

Identical to **shipping-details** (`{{merchant.shippingDetails}}`). It exists because **offer-shipping-details** includes it by this identifier.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
"{{merchant.shippingDetails}}"
```

## Variables and directives

- `{{merchant.shippingDetails}}`: configured shipping policy (object).

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the product page of *Cruise Dual Analog Watch* (simple product, 4 reviews).
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@type": "OfferShippingDetails",
    "shippingRate": {
        "@type": "MonetaryAmount",
        "value": 0,
        "currency": "USD"
    },
    "shippingDestination": {
        "@type": "DefinedRegion",
        "addressCountry": "US"
    }
}
```

## Good to know

- Include-only.
