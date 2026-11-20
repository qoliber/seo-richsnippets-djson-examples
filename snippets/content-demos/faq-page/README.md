# FAQPage (DEMO)

Frequently asked questions with their answers.

| | |
|---|---|
| Identifier | `faq-page` |
| schema.org type | [FAQPage](https://schema.org/FAQPage) |
| Shown on by default | nowhere until you choose: no page type |
| Includes | — |
| Included by | — |
| After install | inactive |

## What it publishes

Three demo questions with answers.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "FAQPage",
    "mainEntity": [
        {
            "@type": "Question",
            "name": "What is your return policy?",
            "acceptedAnswer": {
                "@type": "Answer",
                "text": "We accept returns within 30 days of purchase. Items must be unused and in original packaging."
            }
        },
        {
            "@type": "Question",
            "name": "How long does shipping take?",
            "acceptedAnswer": {
                "@type": "Answer",
                "text": "Standard shipping takes 5-7 business days. Express shipping is available for 2-3 day delivery."
            }
        },
        {
            "@type": "Question",
            "name": "Do you ship internationally?",
            "acceptedAnswer": {
                "@type": "Answer",
                "text": "Yes, we ship to most countries worldwide. International shipping times vary by destination."
            }
        }
    ]
}
```

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "FAQPage",
    "mainEntity": [
        {
            "@type": "Question",
            "name": "What is your return policy?",
            "acceptedAnswer": {
                "@type": "Answer",
                "text": "We accept returns within 30 days of purchase. Items must be unused and in original packaging."
            }
        },
        {
            "@type": "Question",
            "name": "How long does shipping take?",
            "acceptedAnswer": {
                "@type": "Answer",
                "text": "Standard shipping takes 5-7 business days. Express shipping is available for 2-3 day delivery."
            }
        },
        {
            "@type": "Question",
            "name": "Do you ship internationally?",
            "acceptedAnswer": {
                "@type": "Answer",
                "text": "Yes, we ship to most countries worldwide. International shipping times vary by destination."
            }
        }
    ]
}
```

## Good to know

- Google shows FAQ rich results only for well-known government and health sites. The markup is still valid structured data.
- Attach it to the page that actually shows these questions and answers.

_A demo template: its values are examples, not data from your store._
