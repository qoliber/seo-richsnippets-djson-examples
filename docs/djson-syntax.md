# DJSON in snippet templates

Snippet templates are written in **DJSON**: plain JSON plus variables, conditions and loops. This page covers what you can use in a Rich Snippets template. The full language, and its updates, live at **[djson.dev](https://djson.dev)**.

A template must be valid JSON. Every directive is a JSON key and every variable sits inside a JSON string, so the editor and any JSON validator can check your template.

## Variables

Write a variable as `{{path}}`, with dots for nested values: `{{product.name}}`, `{{config.general.store_information.phone}}`.

| You write | You get |
|---|---|
| `"price": "{{commerce.offer.price}}"` | `"price": 55`. A whole-value variable keeps its type: number, text, object or list. |
| `"offers": "{{commerce.offer}}"` | the whole Offer object |
| `"url": "{{config.web.secure.base_url}}about-us"` | `"url": "https://www.example.com/about-us"`. Inside text, the value is pasted in as text. |
| `"name": "{{product.subtitle}}"` with no value | `"name": null` |
| `"text": "Call {{product.subtitle}} now"` with no value | `"text": "Call  now"`. The missing value is left out of the text. |

To leave a property out when there is no value, wrap it in a condition (below) instead of letting it render `null`.

Quote a variable, even when the value is a number or an object: `"{{commerce.offer.price}}"`. That keeps the template valid JSON.

## Including other snippets

`"{{snippet.identifier}}"` pastes in another active snippet:

```json
{
    "@type": "Organization",
    "address": "{{snippet.organization-address}}",
    "sameAs": "{{snippet.organization-social-links}}"
}
```

The module also accepts a bare include as a whole value (`"address": {{snippet.organization-address}}`), but the quoted form keeps the template valid JSON for editors and validators. An inactive or missing include is left out of the parent. Includes nest up to five levels deep, and loops between snippets are refused. See [how snippets work](how-snippets-work.md#1-includes).

## Conditions

A condition is a key whose value is an object. When the condition holds, the object's properties are added to the parent object; otherwise nothing is added.

```json
{
    "@type": "Product",
    "name": "{{product.name}}",
    "@djson if product.ratingValue": {
        "aggregateRating": "{{snippet.aggregate-rating}}"
    }
}
```

A product without ratings publishes just `@type` and `name`.

| Directive | Adds its properties when |
|---|---|
| `"@djson if path"` | the value is truthy |
| `"@djson unless path"` | the value is falsy |
| `"@djson exists path"` | the value exists |
| `"@djson else"` | the `if` directly before it did not apply |

`"0"`, `""`, `0`, `[]`, `null`, `false` and a missing value are falsy. Flags such as `{{product.isConfigurable}}` are `"1"` or `"0"`, so `"@djson if product.isConfigurable"` works as expected.

Conditions can compare values with `==`, `!=`, `>`, `<`, `>=` and `<=`, and combine them with `&&` and `||`:

```json
"@djson if product.reviewCount >= 3": {
    "review": { "@djson for productReviews as review": "{{snippet.review}}" }
}
```

An `if` with an `else`:

```json
{
    "@djson if product.isConfigurable": { "category": "Apparel" },
    "@djson else": { "category": "Accessories" }
}
```

### Choosing between values

`match` picks the first `case` equal to the value, or `default`:

```json
"@djson match system.storeId": {
    "@djson case 1": { "inLanguage": "en" },
    "@djson case 2": { "inLanguage": "de" },
    "@djson default": { "inLanguage": "en" }
}
```

## Loops

`"@djson for list as item"` produces a JSON list with one entry per item. Inside, `item` is the current item:

```json
"itemListElement": {
    "@djson for breadcrumbs as breadcrumb": {
        "@type": "ListItem",
        "position": "{{breadcrumb.position}}",
        "name": "{{breadcrumb.label}}",
        "item": "{{breadcrumb.link}}"
    }
}
```

The entry can also be a whole snippet, which then renders once per item:

```json
"review": { "@djson for productReviews as review": "{{snippet.review}}" }
```

Inside a loop, you can also use:

| Variable | Value |
|---|---|
| `{{_index}}` | position in the list, starting at 0 |
| `{{_key}}` | the item's key |
| `{{_first}}` | `true` for the first item |
| `{{_last}}` | `true` for the last item |

The lists you can loop over are in [variables.md](variables.md#lists-for-loops).

## Functions

DJSON's built-in functions are applied in the function form, as a whole value:

```json
{
    "name": "@djson upper {{product.name}}",
    "brand": "@djson default {{product.manufacturer}} 'Example Store'"
}
```

`upper`, `lower`, `capitalize`, `title`, `trim`, `escape`, `slug`, `substr`, `replace`, `number_format`, `round`, `ceil`,
`floor`, `abs`, `date`, `strtotime`, `count`, `first`, `last`, `join`, `sort`, `unique`, `default` and `coalesce` are
available; DJSON runs them in its sandbox.

## What is not available

- **Pipe expressions.** `{{name | upper}}` and `{{title | default('…')}}` are not applied by the DJSON version the module
  uses (qoliber/djson 1.5): the whole expression is read as a variable name and renders `null`. The editor flags them, and
  saving warns. Use the function form above.

## Tips

- Keep `"@context": "https://schema.org/"` on the snippets that are published on their own. Snippets that are only included, like **offer**, leave it out.
- Guard every optional block with a condition. Google flags empty or zero values such as `"ratingValue": null`.
- Check the result in the page source with **JSON Output Mode** set to **Pretty Print (Debug)**, then test the URL with the [Rich Results Test](https://search.google.com/test/rich-results).

For everything else DJSON can do, see [djson.dev](https://djson.dev).
