# LocalBusiness

A physical shop: contact details, address, opening hours and price range from Store Information.

| | |
|---|---|
| Identifier | `local-business` |
| schema.org type | [LocalBusiness](https://schema.org/LocalBusiness) |
| Shown on by default | Contact Page |
| Includes | [`organization-address`](../../organization/organization-address/) |
| Included by | — |
| After install | inactive |

## What it publishes

Every value comes from configuration and is published only when it is set: the store name, phone and address (Stores → Configuration → General → General → Store Information), the general contact email, the default meta description (Content → Design → Configuration → HTML Head), the header logo, **Store Hours of Operation** (written like `Mo-Fr 09:00-17:00`) and **Price Range**, a field this module adds to Store Information.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "LocalBusiness",
    "@djson if config.general.store_information.name": {
        "name": "{{config.general.store_information.name}}"
    },
    "@djson if config.design.head.default_description": {
        "description": "{{config.design.head.default_description}}"
    },
    "@djson if config.general.store_information.phone": {
        "telephone": "{{config.general.store_information.phone}}"
    },
    "@djson if config.trans_email.ident_general.email": {
        "email": "{{config.trans_email.ident_general.email}}"
    },
    "url": "{{config.web.secure.base_url}}",
    "@djson if config.design.header.logo_src": {
        "logo": "{{config.web.secure.base_url}}media/logo/{{config.design.header.logo_src}}"
    },
    "address": "{{snippet.organization-address}}",
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
- `@djson if config.design.head.default_description`: the block is published only when a default description is set.
- `@djson if config.general.store_information.phone`: the block is published only when a phone number is set.
- `@djson if config.trans_email.ident_general.email`: the block is published only when a general contact email is set.
- `@djson if config.design.header.logo_src`: the block is published only when a header logo is set.
- `@djson if config.general.store_information.hours`: the block is published only when Store Hours of Operation is set.
- `@djson if config.general.store_information.price_range`: the block is published only when Price Range is set.
- `{{config.general.store_information.name}}`: Store Information → Store Name.
- `{{config.design.head.default_description}}`: default meta description (HTML Head).
- `{{config.general.store_information.phone}}`: Store Information → Phone.
- `{{config.trans_email.ident_general.email}}`: General Contact email.
- `{{config.web.secure.base_url}}`: secure base URL.
- `{{config.design.header.logo_src}}`: header logo file.
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
    "@type": "LocalBusiness",
    "name": "Example Store",
    "description": "Outdoor gear, bags and apparel for every day.",
    "telephone": "+1 555 0100",
    "email": "hello@example.com",
    "url": "https://www.example.com/",
    "logo": "https://www.example.com/media/logo/default/logo.png",
    "address": {
        "@type": "PostalAddress",
        "streetAddress": "123 Example Street",
        "addressLocality": "Springfield",
        "postalCode": "12345",
        "addressCountry": "US"
    },
    "openingHours": "Mo-Fr 09:00-17:00",
    "priceRange": "$$"
}
```

## Good to know

- Since Rich Snippets 2.7.0 the template ships without placeholders. An install that still has the older template unedited is updated automatically; an edited one is left alone, and the old version is backed up.
- Add `geo` coordinates or `openingHoursSpecification` yourself if you want them: the shop's location is not in configuration.
- Shown on the Contact Page by default.
