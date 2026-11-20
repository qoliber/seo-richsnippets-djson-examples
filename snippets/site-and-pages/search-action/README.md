# SearchAction

A standalone SearchAction in the EntryPoint form, ready to include.

| | |
|---|---|
| Identifier | `search-action` |
| schema.org type | [SearchAction](https://schema.org/SearchAction) |
| Shown on by default | nowhere on its own: meant to be included |
| Includes | — |
| Included by | — |
| After install | inactive |

## What it publishes

The newer `EntryPoint` / `urlTemplate` form of a site search action, pointing at the catalog search.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@type": "SearchAction",
    "target": {
        "@type": "EntryPoint",
        "urlTemplate": "{{config.web.secure.base_url}}catalogsearch/result/?q={search_term_string}"
    },
    "query-input": "required name=search_term_string"
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
    "@type": "SearchAction",
    "target": {
        "@type": "EntryPoint",
        "urlTemplate": "https://www.example.com/catalogsearch/result/?q={search_term_string}"
    },
    "query-input": "required name=search_term_string"
}
```

## Good to know

- Include-only, and not included by anything by default. To use it, set `"potentialAction": "{{snippet.search-action}}"` in **website**.
