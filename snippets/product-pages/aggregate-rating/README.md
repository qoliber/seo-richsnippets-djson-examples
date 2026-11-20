# Aggregate Rating

The average of the product's approved ratings on a 1–5 scale, with the number of reviews.

| | |
|---|---|
| Identifier | `aggregate-rating` |
| schema.org type | [AggregateRating](https://schema.org/AggregateRating) |
| Shown on by default | nowhere on its own: included by other templates |
| Includes | — |
| Included by | [`product`](../../product-pages/product/) |
| After install | inactive |

## What it publishes

`ratingValue` is the average of the approved rating votes, rounded to one decimal, and `reviewCount` the number of approved reviews.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@type": "AggregateRating",
    "ratingValue": "{{product.ratingSummary}}",
    "reviewCount": "{{product.reviewCount}}",
    "bestRating": "5",
    "worstRating": "1"
}
```

## Variables and directives

- `{{product.ratingSummary}}`: average approved rating, 1–5.
- `{{product.reviewCount}}`: number of approved reviews.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the product page of *Cruise Dual Analog Watch* (simple product, 4 reviews).
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@type": "AggregateRating",
    "ratingValue": "3.3",
    "reviewCount": "4",
    "bestRating": "5",
    "worstRating": "1"
}
```

## Good to know

- Include-only: **product** includes it under `@djson if product.ratingValue`, so a product without votes publishes no rating at all.
