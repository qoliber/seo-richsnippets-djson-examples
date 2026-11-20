# Organization

Your company: name, URL, logo, address, social profiles and customer-service contact.

| | |
|---|---|
| Identifier | `organization` |
| schema.org type | [Organization](https://schema.org/Organization) |
| Shown on by default | Homepage |
| Includes | [`organization-address`](../../organization/organization-address/), [`organization-social-links`](../../organization/organization-social-links/) |
| Included by | [`about-page`](../../site-and-pages/about-page/), [`article`](../../content-demos/article/), [`webpage`](../../site-and-pages/webpage/) |
| After install | inactive |

## What it publishes

Name, phone and address come from Stores → Configuration → General → General → Store Information, and the email from the general contact (Stores → Configuration → General → Store Email Addresses). The address and social profiles are the included templates **organization-address** and **organization-social-links**.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "Organization",
    "name": "{{config.general.store_information.name}}",
    "url": "{{config.web.secure.base_url}}",
    "logo": "{{config.web.secure.base_url}}media/logo/default/logo.svg",
    "address": "{{snippet.organization-address}}",
    "sameAs": "{{snippet.organization-social-links}}",
    "contactPoint": {
        "@type": "ContactPoint",
        "contactType": "customer service",
        "telephone": "{{config.general.store_information.phone}}",
        "email": "{{config.trans_email.ident_general.email}}"
    }
}
```

## Variables and directives

- `{{config.general.store_information.name}}`: Store Information → Store Name.
- `{{config.web.secure.base_url}}`: secure base URL.
- `{{config.general.store_information.phone}}`: Store Information → Phone.
- `{{config.trans_email.ident_general.email}}`: General Contact email.
- `{{snippet.organization-address}}`: the rendered JSON of the [`organization-address`](../../organization/organization-address/) template, when it is active.
- `{{snippet.organization-social-links}}`: the rendered JSON of the [`organization-social-links`](../../organization/organization-social-links/) template, when it is active.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
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
```

## Good to know

- Edit **organization-social-links** before you switch this on: it ships with placeholder profile URLs, which this template would publish.
- The logo path is fixed to `media/logo/default/logo.svg`. Point it at your logo.
- Shown on the Homepage by default.
