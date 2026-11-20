# ItemList

The products of the current category listing, in order.

| | |
|---|---|
| Identifier | `item-list` |
| schema.org type | [ItemList](https://schema.org/ItemList) |
| Shown on by default | Category Page |
| Includes | — |
| Included by | — |
| After install | inactive |

## What it publishes

Loops over `products`, the products of the category listing: position, name and URL of each.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "ItemList",
    "itemListElement": {
        "@djson for products as product": {
            "@type": "ListItem",
            "position": "{{product.position}}",
            "url": "{{product.productUrl}}",
            "name": "{{product.name}}"
        }
    }
}
```

## Variables and directives

- `@djson for products as product`: one entry per item of `products`, the products of the current listing.
- `{{product.position}}`: position in the listing (loop item).
- `{{product.productUrl}}`: product URL.
- `{{product.name}}`: product name.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the category page *Gear › Bags* (14 products). Shown: `itemListElement` is trimmed to 4 of 14 entries.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "ItemList",
    "itemListElement": [
        {
            "@type": "ListItem",
            "position": "1",
            "url": "https://www.example.com/joust-duffle-bag.html",
            "name": "Joust Duffle Bag"
        },
        {
            "@type": "ListItem",
            "position": "2",
            "url": "https://www.example.com/strive-shoulder-pack.html",
            "name": "Strive Shoulder Pack"
        },
        {
            "@type": "ListItem",
            "position": "3",
            "url": "https://www.example.com/crown-summit-backpack.html",
            "name": "Crown Summit Backpack"
        },
        {
            "@type": "ListItem",
            "position": "4",
            "url": "https://www.example.com/wayfarer-messenger-bag.html",
            "name": "Wayfarer Messenger Bag"
        }
    ]
}
```

## Good to know

- Shown on Category pages by default.
