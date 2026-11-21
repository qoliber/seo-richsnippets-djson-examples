# WebPage

The page it is published on: its title, meta description and URL, with the organization as publisher.

| | |
|---|---|
| Identifier | `webpage` |
| schema.org type | [WebPage](https://schema.org/WebPage) |
| Shown on by default | nowhere until you choose: no page type |
| Includes | [`organization`](../../organization/organization/) |
| Included by | — |
| After install | inactive |

## What it publishes

`page.title`, `page.description` and `page.url` are the current page's title, meta description and canonical URL (or its URL without the query), each published only when set. The example output is the home page.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "WebPage",
    "@djson if page.title": {
        "name": "{{page.title}}"
    },
    "@djson if page.description": {
        "description": "{{page.description}}"
    },
    "@djson if page.url": {
        "url": "{{page.url}}"
    },
    "publisher": "{{snippet.organization}}"
}
```

## Variables and directives

- `@djson if page.title`: the block is published only when the page has a title.
- `@djson if page.description`: the block is published only when the page has a meta description.
- `@djson if page.url`: the block is published only when the page has a URL.
- `{{page.title}}`: the page title.
- `{{page.description}}`: the page meta description.
- `{{page.url}}`: the canonical URL, or the current URL without its query.
- `{{snippet.organization}}`: the rendered JSON of the [`organization`](../../organization/organization/) template, when it is active.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "WebPage",
    "name": "Home Page",
    "description": "Example Store: outdoor gear, bags and apparel.",
    "url": "https://www.example.com/",
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

- Rich Snippets 2.6.2 and earlier had no `page.*` values, so this template published `null` (GitLab seo-rich-snippets#4). 2.7.0 provides them and updates the unedited shipped template.
- Has no page type: choose where it appears.
