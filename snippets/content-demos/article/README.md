# Article (DEMO)

A blog article with author and publisher.

| | |
|---|---|
| Identifier | `article` |
| schema.org type | [Article](https://schema.org/Article) |
| Shown on by default | nowhere until you choose: no page type |
| Includes | [`organization`](../../organization/organization/) |
| Included by | — |
| After install | inactive |

## What it publishes

Fixed demo values: headline, description, image, dates and author, with **organization** as publisher.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "Article",
    "headline": "10 Tips for Choosing the Perfect Product",
    "description": "Discover expert tips on selecting the right products for your needs with our comprehensive buying guide.",
    "image": "{{config.web.secure.base_url}}media/blog/article-image.jpg",
    "datePublished": "2024-01-15T08:00:00+00:00",
    "dateModified": "2024-01-20T10:30:00+00:00",
    "author": {
        "@type": "Person",
        "name": "Expert Team"
    },
    "publisher": "{{snippet.organization}}"
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
    "@type": "Article",
    "headline": "10 Tips for Choosing the Perfect Product",
    "description": "Discover expert tips on selecting the right products for your needs with our comprehensive buying guide.",
    "image": "https://www.example.com/media/blog/article-image.jpg",
    "datePublished": "2024-01-15T08:00:00+00:00",
    "dateModified": "2024-01-20T10:30:00+00:00",
    "author": {
        "@type": "Person",
        "name": "Expert Team"
    },
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

- A demo to copy: create one template per article page, attach it with a **Custom URL Pattern** or **Specific CMS Pages**, and write your own values.

_A demo template: its values are examples, not data from your store._
