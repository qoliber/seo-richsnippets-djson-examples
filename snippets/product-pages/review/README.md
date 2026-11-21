# Review

One approved customer review: rating, author, text and date.

| | |
|---|---|
| Identifier | `review` |
| schema.org type | [Review](https://schema.org/Review) |
| Shown on by default | nowhere on its own: included by other templates |
| Includes | — |
| Included by | [`product`](../../product-pages/product/) |
| After install | inactive |

## What it publishes

**product** renders this template once for every approved review of the product: `"@djson for productReviews as review": "{{snippet.review}}"`. Inside the loop, `review` is the current review.

`reviewRating` is added only when the review carries a rating vote.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@type": "Review",
    "@djson if review.rating": {
        "reviewRating": { "@type": "Rating", "ratingValue": "{{review.rating}}", "bestRating": "5" }
    },
    "author": { "@type": "Person", "name": "{{review.nickname}}" },
    "reviewBody": "{{review.detail}}",
    "datePublished": "{{review.createdAt}}"
}
```

## Variables and directives

- `@djson if review.rating`: the block is published only when the review has a rating vote.
- `{{review.rating}}`: the review's rating, 1–5.
- `{{review.nickname}}`: author nickname.
- `{{review.detail}}`: review text.
- `{{review.createdAt}}`: review date.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the product page of *Cruise Dual Analog Watch* (simple product, 4 reviews). Shown: the first of the product's four reviews, as **product** renders it in its `productReviews` loop.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@type": "Review",
    "reviewRating": {
        "@type": "Rating",
        "ratingValue": "5",
        "bestRating": "5"
    },
    "author": {
        "@type": "Person",
        "name": "Frank"
    },
    "reviewBody": "When I'm in another country, I hate not knowing what time it really is back home so the dual time zone settings are awesome!",
    "datePublished": "2026-09-23T22:16:20+02:00"
}
```

## Good to know

- Include-only, and only meaningful inside the `productReviews` loop.
- `datePublished` is the review's creation time in ISO 8601, in the store's time zone (Rich Snippets 2.7.0).
- If this template is inactive, the product leaves out its whole `review` property rather than publishing an empty list.
