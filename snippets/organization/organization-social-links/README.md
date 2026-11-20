# Organization Social Links

The list of your social profile URLs, for the organization's sameAs.

| | |
|---|---|
| Identifier | `organization-social-links` |
| schema.org type | sameAs (list of URLs) |
| Shown on by default | nowhere on its own: included by other templates |
| Includes | — |
| Included by | [`organization`](../../organization/organization/) |
| After install | inactive |

## What it publishes

A plain JSON array of profile URLs. It is the only template that is a list rather than an object.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
[
    "https://www.facebook.com/yourpage",
    "https://www.instagram.com/yourpage",
    "https://www.twitter.com/yourpage",
    "https://www.linkedin.com/company/yourcompany",
    "https://www.youtube.com/channel/yourchannel"
]
```

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
[
    "https://www.facebook.com/yourpage",
    "https://www.instagram.com/yourpage",
    "https://www.twitter.com/yourpage",
    "https://www.linkedin.com/company/yourcompany",
    "https://www.youtube.com/channel/yourchannel"
]
```

## Good to know

- Ships with placeholder URLs (`https://www.facebook.com/yourpage` …). Replace them with your profiles, or remove the ones you do not have.
- Include-only: used by **organization**.
