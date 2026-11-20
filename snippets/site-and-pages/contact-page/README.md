# ContactPage (DEMO)

Your Contact page, with a customer-service contact point.

| | |
|---|---|
| Identifier | `contact-page` |
| schema.org type | [ContactPage](https://schema.org/ContactPage) |
| Shown on by default | Contact Page |
| Includes | — |
| Included by | — |
| After install | inactive |

## What it publishes

Store name, phone and general contact email from configuration; the page URL is `contact` under your base URL.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "ContactPage",
    "name": "Contact Us",
    "description": "Get in touch with our team",
    "url": "{{config.web.secure.base_url}}contact",
    "mainEntity": {
        "@type": "Organization",
        "name": "{{config.general.store_information.name}}",
        "contactPoint": {
            "@type": "ContactPoint",
            "telephone": "{{config.general.store_information.phone}}",
            "email": "{{config.trans_email.ident_general.email}}",
            "contactType": "Customer Service",
            "availableLanguage": ["English", "Spanish", "French"]
        }
    }
}
```

## Variables and directives

- `{{config.web.secure.base_url}}`: secure base URL.
- `{{config.general.store_information.name}}`: Store Information → Store Name.
- `{{config.general.store_information.phone}}`: Store Information → Phone.
- `{{config.trans_email.ident_general.email}}`: General Contact email.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "ContactPage",
    "name": "Contact Us",
    "description": "Get in touch with our team",
    "url": "https://www.example.com/contact",
    "mainEntity": {
        "@type": "Organization",
        "name": "Example Store",
        "contactPoint": {
            "@type": "ContactPoint",
            "telephone": "+1 555 0100",
            "email": "hello@example.com",
            "contactType": "Customer Service",
            "availableLanguage": [
                "English",
                "Spanish",
                "French"
            ]
        }
    }
}
```

## Good to know

- `availableLanguage` is a demo list (English, Spanish, French). Set the languages you support.
- Shown on the Contact Page by default.
