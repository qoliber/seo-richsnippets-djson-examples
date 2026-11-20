# Product

The product itself: name, description, SKU, image and brand, with its offer, rating and reviews when it has them.

| | |
|---|---|
| Identifier | `product` |
| schema.org type | [Product](https://schema.org/Product) |
| Shown on by default | Product Page |
| Includes | [`offer`](../../product-pages/offer/), [`aggregate-rating`](../../product-pages/aggregate-rating/), [`review`](../../product-pages/review/) |
| Included by | — |
| After install | inactive |

## What it publishes

The main template of a product page. Each optional block is guarded by a condition, so the page never publishes an empty or zero value: the offer appears only when the product has one, the rating only when it has approved votes, and the reviews only when there are approved reviews.

On a configurable product with **product-group** switched on, this Product is folded into the ProductGroup, so the page publishes a single ProductGroup instead of two nodes (see [product-group](../product-group/)).

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "Product",
    "name": "{{product.name}}",
    "description": "{{product.shortDescription}}",
    "sku": "{{product.sku}}",
    "image": "{{product.image}}",
    "@djson if product.manufacturer": {
        "brand": {
            "@type": "Brand",
            "name": "{{product.manufacturer}}"
        }
    },
    "@djson if commerce.offer": {
        "offers": "{{snippet.offer}}"
    },
    "@djson if product.ratingValue": {
        "aggregateRating": "{{snippet.aggregate-rating}}"
    },
    "@djson if product.reviewCount": {
        "review": {
            "@djson for productReviews as review": "{{snippet.review}}"
        }
    }
}
```

## Variables and directives

- `@djson for productReviews as review`: one entry per item of `productReviews`, the product's approved reviews.
- `@djson if product.manufacturer`: the block is published only when the product has a manufacturer.
- `@djson if commerce.offer`: the block is published only when the product has an offer.
- `@djson if product.ratingValue`: the block is published only when the product has approved rating votes.
- `@djson if product.reviewCount`: the block is published only when the product has approved reviews.
- `{{product.name}}`: product name.
- `{{product.shortDescription}}`: short description as plain text.
- `{{product.sku}}`: SKU.
- `{{product.image}}`: base image URL.
- `{{product.manufacturer}}`: manufacturer (option label).
- `{{snippet.offer}}`: the rendered JSON of the [`offer`](../../product-pages/offer/) template, when it is active.
- `{{snippet.aggregate-rating}}`: the rendered JSON of the [`aggregate-rating`](../../product-pages/aggregate-rating/) template, when it is active.
- `{{snippet.review}}`: the rendered JSON of the [`review`](../../product-pages/review/) template, when it is active.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the product page of *Cruise Dual Analog Watch* (simple product, 4 reviews).
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "Product",
    "name": "Cruise Dual Analog Watch",
    "description": "Whether you're traveling or wish you were, you'll never let time zones perplex you again with the Cruise Dual Analog Watch. The thick, adjustable band promises a comfortable, personalized fit to this classy, modern time piece. Two dials. Stainless steel case. Adjustable leather band.",
    "sku": "24-MG05",
    "image": "https://www.example.com/media/catalog/product/cache/6517c62f5899ad6aa0ba23ceb3eeff97/m/g/mg05-br-0.jpg",
    "offers": {
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
    },
    "aggregateRating": {
        "@type": "AggregateRating",
        "ratingValue": "3.3",
        "reviewCount": "4",
        "bestRating": "5",
        "worstRating": "1"
    },
    "review": [
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
            "datePublished": "2026-09-23 20:16:20"
        },
        {
            "@type": "Review",
            "reviewRating": {
                "@type": "Rating",
                "ratingValue": "4",
                "bestRating": "5"
            },
            "author": {
                "@type": "Person",
                "name": "Jamie"
            },
            "reviewBody": "Really perfect for my needs. I travel a ton, so I'll always know what time to give my wife a call back home.",
            "datePublished": "2026-09-23 20:16:20"
        },
        {
            "@type": "Review",
            "reviewRating": {
                "@type": "Rating",
                "ratingValue": "2",
                "bestRating": "5"
            },
            "author": {
                "@type": "Person",
                "name": "Bobby"
            },
            "reviewBody": "I really like the modern look of this watch, but I could only get one time zone to work. I hope it has a warranty because I'm sending it back!",
            "datePublished": "2026-09-23 20:16:20"
        },
        {
            "@type": "Review",
            "reviewRating": {
                "@type": "Rating",
                "ratingValue": "2",
                "bestRating": "5"
            },
            "author": {
                "@type": "Person",
                "name": "Tommie"
            },
            "reviewBody": "This watch is so tight around my wrist! I don't care if it's adjustable, it cuts off my circulation.",
            "datePublished": "2026-09-23 20:16:20"
        }
    ]
}
```

## Good to know

- `description` is the short description as plain text (HTML removed).
- The brand comes from the `manufacturer` attribute. If your catalogue keeps the brand in another attribute, use its code, for example `{{product.brand}}`.
- Switch on **offer**, **aggregate-rating** and **review** as well: an include that is inactive is left out of the product.
- A product with no offer, no rating and no reviews (a grouped product without reviews, a bundle that cannot be bought) is not published at all, because Google rejects a Product without any of them.
