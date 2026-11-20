# Organization Address

Your postal address from Store Information.

| | |
|---|---|
| Identifier | `organization-address` |
| schema.org type | [PostalAddress](https://schema.org/PostalAddress) |
| Shown on by default | nowhere on its own: included by other templates |
| Includes | — |
| Included by | [`local-business`](../../organization/local-business/), [`organization`](../../organization/organization/), [`store`](../../organization/store/) |
| After install | inactive |

## What it publishes

Street (line 1), city, postcode and country from Store Information.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@type": "PostalAddress",
    "streetAddress": "{{config.general.store_information.street_line1}}",
    "addressLocality": "{{config.general.store_information.city}}",
    "postalCode": "{{config.general.store_information.postcode}}",
    "addressCountry": "{{config.general.store_information.country_id}}"
}
```

## Variables and directives

- `{{config.general.store_information.street_line1}}`: Store Information → Street Address.
- `{{config.general.store_information.city}}`: Store Information → City.
- `{{config.general.store_information.postcode}}`: Store Information → ZIP/Postal Code.
- `{{config.general.store_information.country_id}}`: Store Information → Country.

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@type": "PostalAddress",
    "streetAddress": "123 Example Street",
    "addressLocality": "Springfield",
    "postalCode": "12345",
    "addressCountry": "US"
}
```

## Good to know

- Include-only: used by **organization**, **local-business** and **store**.
