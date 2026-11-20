# AboutPage

Your About page, with the organization as its main entity.

| | |
|---|---|
| Identifier | `about-page` |
| schema.org type | [AboutPage](https://schema.org/AboutPage) |
| Shown on by default | nowhere until you choose: no page type |
| Includes | [`organization`](../../organization/organization/) |
| Included by | — |
| After install | inactive |

## What it publishes

Fixed name and description, the URL `about-us` under your base URL, and the included **organization**.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "AboutPage",
    "name": "About Us",
    "description": "Learn more about our company and mission",
    "url": "{{config.web.secure.base_url}}about-us",
    "mainEntity": "{{snippet.organization}}"
}
```

## Variables and directives

- `{{config.web.secure.base_url}}`: secure base URL.
- `{{snippet.organization}}`: the rendered JSON of the [`organization`](../../organization/organization/) template, when it is active.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "AboutPage",
    "name": "About Us",
    "description": "Learn more about our company and mission",
    "url": "https://www.example.com/about-us",
    "mainEntity": {
        "@context": "https://schema.org/",
        "@type": "Organization",
        "name": "Example Store",
        "url": "https://www.example.com/",
        "logo": "https://www.example.com/media/logo/default/logo.svg",
        "address": {
            "@type": "PostalAddress",
            "streetAddress": "123 Example Street",
            "addressLocality": "Springfield",
            "postalCode": "12345",
            "addressCountry": "US"
        },
        "sameAs": [
            "https://www.facebook.com/yourpage",
            "https://www.instagram.com/yourpage",
            "https://www.twitter.com/yourpage",
            "https://www.linkedin.com/company/yourcompany",
            "https://www.youtube.com/channel/yourchannel"
        ],
        "contactPoint": {
            "@type": "ContactPoint",
            "contactType": "customer service",
            "telephone": "+1 555 0100",
            "email": "hello@example.com"
        }
    }
}
```

## Good to know

- Has no page type. Attach it to your About CMS page under **Specific CMS Pages**, or a **Custom URL Pattern** such as `/about-us`, and edit the text and URL.
