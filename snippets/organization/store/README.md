# Store

A retail shop with its address, coordinates and weekly opening hours.

| | |
|---|---|
| Identifier | `store` |
| schema.org type | [Store](https://schema.org/Store) |
| Shown on by default | nowhere until you choose: no page type |
| Includes | [`organization-address`](../../organization/organization-address/) |
| Included by | — |
| After install | inactive |

## What it publishes

Uses Store Information for the name, phone and address.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "Store",
    "name": "{{config.general.store_information.name}}",
    "image": "{{config.web.secure.base_url}}media/store/storefront.jpg",
    "telephone": "{{config.general.store_information.phone}}",
    "address": "{{snippet.organization-address}}",
    "geo": {
        "@type": "GeoCoordinates",
        "latitude": "40.7128",
        "longitude": "-74.0060"
    },
    "url": "{{config.web.secure.base_url}}",
    "openingHoursSpecification": {
        "@djson for storeHours as hours": {
            "@type": "OpeningHoursSpecification",
            "dayOfWeek": "{{hours.day}}",
            "opens": "{{hours.open}}",
            "closes": "{{hours.close}}"
        }
    }
}
```

## Variables and directives

- `@djson for storeHours as hours`: one entry per item of `storeHours`, no data in 2.6.2: the loop renders an empty list.
- `{{config.general.store_information.name}}`: Store Information → Store Name.
- `{{config.web.secure.base_url}}`: secure base URL.
- `{{config.general.store_information.phone}}`: Store Information → Phone.
- `{{hours.day}}`: loop item of storeHours (no data in 2.6.2).
- `{{hours.open}}`: loop item of storeHours (no data in 2.6.2).
- `{{hours.close}}`: loop item of storeHours (no data in 2.6.2).
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
    "image": "https://www.example.com/media/store/storefront.jpg",
    "telephone": "+1 555 0100",
    "address": {
        "@type": "PostalAddress",
        "streetAddress": "123 Example Street",
        "addressLocality": "Springfield",
        "postalCode": "12345",
        "addressCountry": "US"
    },
    "geo": {
        "@type": "GeoCoordinates",
        "latitude": "40.7128",
        "longitude": "-74.0060"
    },
    "url": "https://www.example.com/",
    "openingHoursSpecification": []
}
```

## Good to know

- The coordinates and the image path are placeholders.
- `storeHours` has no data in Rich Snippets 2.6.2, so `openingHoursSpecification` renders an empty list. Write the hours as fixed `OpeningHoursSpecification` objects instead.
- Has no page type: choose where it appears, for example a CMS page or a custom URL pattern.
