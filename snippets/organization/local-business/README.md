# LocalBusiness

A physical shop: contact details, address, coordinates, opening hours and price range.

| | |
|---|---|
| Identifier | `local-business` |
| schema.org type | [LocalBusiness](https://schema.org/LocalBusiness) |
| Shown on by default | Contact Page |
| Includes | [`organization-address`](../../organization/organization-address/) |
| Included by | — |
| After install | inactive |

## What it publishes

Uses Store Information for the name, phone and address, and the general contact email.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "LocalBusiness",
    "name": "{{config.general.store_information.name}}",
    "description": "{{store.description}}",
    "telephone": "{{config.general.store_information.phone}}",
    "email": "{{config.trans_email.ident_general.email}}",
    "url": "{{config.web.secure.base_url}}",
    "logo": "{{config.web.secure.base_url}}media/logo/default/logo.svg",
    "image": "{{config.web.secure.base_url}}media/store/storefront.jpg",
    "address": "{{snippet.organization-address}}",
    "geo": {
        "@type": "GeoCoordinates",
        "latitude": "40.7128",
        "longitude": "-74.0060"
    },
    "openingHours": "Mo-Fr 10:00-18:00",
    "priceRange": "$$"
}
```

## Variables and directives

- `{{config.general.store_information.name}}`: Store Information → Store Name.
- `{{store.description}}`: no value in 2.6.2 (renders null).
- `{{config.general.store_information.phone}}`: Store Information → Phone.
- `{{config.trans_email.ident_general.email}}`: General Contact email.
- `{{config.web.secure.base_url}}`: secure base URL.
- `{{snippet.organization-address}}`: the rendered JSON of the [`organization-address`](../../organization/organization-address/) template, when it is active.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "LocalBusiness",
    "name": "Example Store",
    "description": null,
    "telephone": "+1 555 0100",
    "email": "hello@example.com",
    "url": "https://www.example.com/",
    "logo": "https://www.example.com/media/logo/default/logo.svg",
    "image": "https://www.example.com/media/store/storefront.jpg",
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
    "openingHours": "Mo-Fr 10:00-18:00",
    "priceRange": "$$"
}
```

## Good to know

- Several values are placeholders to replace: the coordinates (40.7128, −74.0060), `openingHours`, `priceRange`, and the image path.
- `openingHours` and `priceRange` can come from Store Information instead: `{{config.general.store_information.hours}}` (Store Hours of Operation, written like `Mo-Fr 10:00-18:00`) and `{{config.general.store_information.price_range}}` (Price Range, a field this module adds to Store Information).
- `{{store.description}}` has no value in Rich Snippets 2.6.2, so `description` renders `null`. Write the description as text.
- Shown on the Contact Page by default.
