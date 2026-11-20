# Shipping Details

Your configured shipping rate and destination, for the offer.

| | |
|---|---|
| Identifier | `shipping-details` |
| schema.org type | [OfferShippingDetails](https://schema.org/OfferShippingDetails) |
| Shown on by default | nowhere on its own: included by other templates |
| Includes | — |
| Included by | [`offer`](../../product-pages/offer/) |
| After install | inactive |

## What it publishes

The template is the single placeholder `{{merchant.shippingDetails}}`, built from Stores → Configuration → Qoliber → SEO: Rich Snippets → Merchant Shipping and Returns: **Shipping Destination** and **Shipping Rate in Base Currency** (an explicit `0` means free shipping; the base-currency rate is converted to the storefront currency).

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

- Include-only: **offer** includes it under `@djson if merchant.shippingDetails`.
- Nothing is published until **Emit Configured Shipping Policy** is Yes: an unconfigured promise is never invented.
