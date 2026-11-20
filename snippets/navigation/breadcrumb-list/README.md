# BreadcrumbList

The page's breadcrumb trail, from the home page to the current page.

| | |
|---|---|
| Identifier | `breadcrumb-list` |
| schema.org type | [BreadcrumbList](https://schema.org/BreadcrumbList) |
| Shown on by default | Category Page, Product Page |
| Includes | — |
| Included by | — |
| After install | inactive |

## What it publishes

Loops over `breadcrumbs`, the same trail Magento shows on the page: one `ListItem` per crumb with its position, label and link. The last crumb, the current page, links to the page's own URL.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "BreadcrumbList",
    "itemListElement": {
        "@djson for breadcrumbs as breadcrumb": {
            "@type": "ListItem",
            "position": "{{breadcrumb.position}}",
            "name": "{{breadcrumb.label}}",
            "item": "{{breadcrumb.link}}"
        }
    }
}
```

## Variables and directives

- `@djson for breadcrumbs as breadcrumb`: one entry per item of `breadcrumbs`, the page's breadcrumb trail.
- `{{breadcrumb.position}}`: crumb position.
- `{{breadcrumb.label}}`: crumb label.
- `{{breadcrumb.link}}`: crumb URL.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the category page *Gear › Bags* (14 products).
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "BreadcrumbList",
    "itemListElement": [
        {
            "@type": "ListItem",
            "position": "1",
            "name": "Home",
            "item": "https://www.example.com/"
        },
        {
            "@type": "ListItem",
            "position": "2",
            "name": "Gear",
            "item": "https://www.example.com/gear.html"
        },
        {
            "@type": "ListItem",
            "position": "3",
            "name": "Bags",
            "item": "https://www.example.com/gear/bags.html"
        }
    ]
}
```

## Good to know

- Shown on Category and Product pages by default. On a product page reached from a category, the trail includes that category.
