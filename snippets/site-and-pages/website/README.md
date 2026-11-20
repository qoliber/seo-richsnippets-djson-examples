# WebSite

Your website, with a SearchAction pointing at the catalog search.

| | |
|---|---|
| Identifier | `website` |
| schema.org type | [WebSite](https://schema.org/WebSite) |
| Shown on by default | Homepage |
| Includes | — |
| Included by | — |
| After install | inactive |

## What it publishes

The site URL and a `SearchAction` whose target is the catalog search results page.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "WebSite",
    "url": "{{config.web.secure.base_url}}",
    "potentialAction": {
        "@type": "SearchAction",
        "target": "{{config.web.secure.base_url}}catalogsearch/result/?q={q}",
        "query-input": "required name=q"
    }
}
```

## Variables and directives

- `{{config.web.secure.base_url}}`: secure base URL.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "WebSite",
    "url": "https://www.example.com/",
    "potentialAction": {
        "@type": "SearchAction",
        "target": "https://www.example.com/catalogsearch/result/?q={q}",
        "query-input": "required name=q"
    }
}
```

## Good to know

- Google uses WebSite markup on the home page to pick your site name; add `"name": "{{config.general.store_information.name}}"` for that.
- Google no longer shows the sitelinks search box, so the SearchAction is optional.
- Shown on the Homepage by default.
