# Store

A retail shop with its address, opening hours and price range from Store Information.

| | |
|---|---|
| Identifier | `store` |
| schema.org type | [Store](https://schema.org/Store) |
| Shown on by default | nowhere until you choose: no page type |
| Includes | [`organization-address`](../../organization/organization-address/) |
| Included by | — |
| After install | inactive |

## What it publishes

Name, phone, address, opening hours and price range from Store Information, each published only when set.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "Store",
    "@djson if config.general.store_information.name": {
        "name": "{{config.general.store_information.name}}"
    },
    "@djson if config.general.store_information.phone": {
        "telephone": "{{config.general.store_information.phone}}"
    },
    "address": "{{snippet.organization-address}}",
    "url": "{{config.web.secure.base_url}}",
    "@djson if config.general.store_information.hours": {
        "openingHours": "{{config.general.store_information.hours}}"
    },
    "@djson if config.general.store_information.price_range": {
        "priceRange": "{{config.general.store_information.price_range}}"
    }
}
```

## Variables and directives

- `@djson if config.general.store_information.name`: the block is published only when a store name is set.
- `@djson if config.general.store_information.phone`: the block is published only when a phone number is set.
- `@djson if config.general.store_information.hours`: the block is published only when Store Hours of Operation is set.
- `@djson if config.general.store_information.price_range`: the block is published only when Price Range is set.
- `{{config.general.store_information.name}}`: Store Information → Store Name.
- `{{config.general.store_information.phone}}`: Store Information → Phone.
- `{{config.web.secure.base_url}}`: secure base URL.
- `{{config.general.store_information.hours}}`: Store Information → Store Hours of Operation.
- `{{config.general.store_information.price_range}}`: Store Information → Price Range.
- `{{snippet.organization-address}}`: the rendered JSON of the [`organization-address`](../../organization/organization-address/) template, when it is active.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "Store",
    "name": "Example Store",
    "telephone": "+1 555 0100",
    "address": {
        "@type": "PostalAddress",
        "streetAddress": "123 Example Street",
        "addressLocality": "Springfield",
        "postalCode": "12345",
        "addressCountry": "US"
    },
    "url": "https://www.example.com/",
    "openingHours": "Mo-Fr 09:00-17:00",
    "priceRange": "$$"
}
```

## Good to know

- Since Rich Snippets 2.7.0 the template has no placeholder coordinates or image, and no opening-hours loop without data.
- Has no page type: choose where it appears, for example a CMS page or a custom URL pattern.
