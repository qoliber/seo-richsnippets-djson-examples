# WebPage

A generic web page with the organization as publisher.

| | |
|---|---|
| Identifier | `webpage` |
| schema.org type | [WebPage](https://schema.org/WebPage) |
| Shown on by default | nowhere until you choose: no page type |
| Includes | [`organization`](../../organization/organization/) |
| Included by | — |
| After install | inactive |

## What it publishes

A WebPage node whose `publisher` is the included **organization**.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "WebPage",
    "name": "{{page.title}}",
    "description": "{{page.description}}",
    "url": "{{page.url}}",
    "publisher": "{{snippet.organization}}"
}
```

## Variables and directives

- `{{page.title}}`: no value in 2.6.2 (renders null).
- `{{page.description}}`: no value in 2.6.2 (renders null).
- `{{page.url}}`: no value in 2.6.2 (renders null).
- `{{snippet.organization}}`: the rendered JSON of the [`organization`](../../organization/organization/) template, when it is active.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "WebPage",
    "name": null,
    "description": null,
    "url": null,
    "publisher": {
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

- `{{page.title}}`, `{{page.description}}` and `{{page.url}}` have no value in Rich Snippets 2.6.2, so they render `null`. Write them as text for the page you target, or leave the template off.
- Has no page type: choose where it appears.
