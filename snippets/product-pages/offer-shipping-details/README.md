# OfferShippingDetails

An alternative, self-contained Product with an inline Offer and shipping and return policies.

| | |
|---|---|
| Identifier | `offer-shipping-details` |
| schema.org type | [Product](https://schema.org/Product) |
| Shown on by default | Product Page |
| Includes | [`shipping-rate-settings`](../../shipping-and-returns/shipping-rate-settings/), [`merchant-return-policy`](../../shipping-and-returns/merchant-return-policy/) |
| Included by | — |
| After install | inactive |

## What it publishes

An example of writing the offer by hand instead of including **offer**: price from `{{product.finalPrice}}`, currency from `{{store.currencyCode}}`, and the shipping and return policies from **shipping-rate-settings** and **merchant-return-policy**.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "Product",
    "name": "{{product.name}}",
    "sku": "{{product.sku}}",
    "offers": {
        "@type": "Offer",
        "price": "{{product.finalPrice}}",
        "priceCurrency": "{{store.currencyCode}}",
        "availability": "https://schema.org/InStock",
        "url": "{{product.productUrl}}",
        "@djson if merchant.shippingDetails": {
            "shippingDetails": "{{snippet.shipping-rate-settings}}"
        },
        "@djson if merchant.returnPolicy": {
            "hasMerchantReturnPolicy": "{{snippet.merchant-return-policy}}"
        }
    }
}
```

## Variables and directives

- `@djson if merchant.shippingDetails`: the block is published only when a shipping policy is configured.
- `@djson if merchant.returnPolicy`: the block is published only when a return policy is configured.
- `{{product.name}}`: product name.
- `{{product.sku}}`: SKU.
- `{{product.finalPrice}}`: final price as the page shows it.
- `{{store.currencyCode}}`: storefront currency code.
- `{{product.productUrl}}`: product URL.
- `{{snippet.shipping-rate-settings}}`: the rendered JSON of the [`shipping-rate-settings`](../../shipping-and-returns/shipping-rate-settings/) template, when it is active.
- `{{snippet.merchant-return-policy}}`: the rendered JSON of the [`merchant-return-policy`](../../shipping-and-returns/merchant-return-policy/) template, when it is active.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the product page of *Cruise Dual Analog Watch* (simple product, 4 reviews).
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "Product",
    "name": "Cruise Dual Analog Watch",
    "sku": "24-MG05",
    "offers": {
        "@type": "Offer",
        "price": "55",
        "priceCurrency": "USD",
        "availability": "https://schema.org/InStock",
        "url": "https://www.example.com/cruise-dual-analog-watch.html",
        "shippingDetails": {
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
        },
        "hasMerchantReturnPolicy": {
            "@type": "MerchantReturnPolicy",
            "applicableCountry": "US",
            "returnPolicyCategory": "https://schema.org/MerchantReturnFiniteReturnWindow",
            "merchantReturnDays": 30,
            "returnMethod": "https://schema.org/ReturnByMail",
            "returnFees": "https://schema.org/FreeReturn"
        }
    }
}
```

## Good to know

- Do not switch it on together with **product**: both publish a Product on the Product Page, so the page would carry two.
- `availability` is fixed to `InStock`. The shipped **product** + **offer** pair uses the real stock status and the per-type pricing rules; prefer it.
