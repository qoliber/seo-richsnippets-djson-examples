# Offer

The offer the product page makes: price, currency, availability and URL, plus your shipping and return policies.

| | |
|---|---|
| Identifier | `offer` |
| schema.org type | [Offer](https://schema.org/Offer) |
| Shown on by default | nowhere on its own: included by other templates |
| Includes | [`shipping-details`](../../shipping-and-returns/shipping-details/), [`merchant-return-policy`](../../shipping-and-returns/merchant-return-policy/) |
| Included by | [`product`](../../product-pages/product/) |
| After install | inactive |

## What it publishes

Renders `commerce.offer`, the single Offer the module computes for the current product at the price the page shows, with the store's tax display and currency. Simple, virtual and downloadable products offer one unit; a bundle offers its cheapest purchasable configuration; a configurable offers the lowest price of its in-stock variants. Grouped products have no offer, so the whole template renders nothing for them.

When you publish shipping and return policies (Stores → Configuration → Qoliber → SEO: Rich Snippets → Merchant Shipping and Returns), the offer gains `shippingDetails` and `hasMerchantReturnPolicy`.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@djson if commerce.offer": {
        "@type": "Offer",
        "url": "{{commerce.offer.url}}",
        "price": "{{commerce.offer.price}}",
        "priceCurrency": "{{commerce.offer.priceCurrency}}",
        "availability": "{{commerce.offer.availability}}",
        "@djson if merchant.shippingDetails": {
            "shippingDetails": "{{snippet.shipping-details}}"
        },
        "@djson if merchant.returnPolicy": {
            "hasMerchantReturnPolicy": "{{snippet.merchant-return-policy}}"
        }
    }
}
```

## Variables and directives

- `@djson if commerce.offer`: the block is published only when the product has an offer.
- `@djson if merchant.shippingDetails`: the block is published only when a shipping policy is configured.
- `@djson if merchant.returnPolicy`: the block is published only when a return policy is configured.
- `{{commerce.offer.url}}`: offer URL.
- `{{commerce.offer.price}}`: price the page shows.
- `{{commerce.offer.priceCurrency}}`: storefront currency.
- `{{commerce.offer.availability}}`: schema.org availability URL.
- `{{snippet.shipping-details}}`: the rendered JSON of the [`shipping-details`](../../shipping-and-returns/shipping-details/) template, when it is active.
- `{{snippet.merchant-return-policy}}`: the rendered JSON of the [`merchant-return-policy`](../../shipping-and-returns/merchant-return-policy/) template, when it is active.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the product page of *Cruise Dual Analog Watch* (simple product, 4 reviews).
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@type": "Offer",
    "url": "https://www.example.com/cruise-dual-analog-watch.html",
    "price": 55,
    "priceCurrency": "USD",
    "availability": "https://schema.org/InStock",
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
```

## Good to know

- Include-only: it has no page type and is published inside **product** (`"offers": "{{snippet.offer}}"`).
- The module never publishes an `AggregateOffer`; Google advises against it for product variants.
- Google merchant listings need a price above zero.
