# QAPage (DEMO)

A page built around one question and its answers.

| | |
|---|---|
| Identifier | `qa-page` |
| schema.org type | [QAPage](https://schema.org/QAPage) |
| Shown on by default | nowhere until you choose: no page type |
| Includes | — |
| Included by | — |
| After install | inactive |

## What it publishes

A demo question with an accepted answer, vote counts and dates.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "QAPage",
    "mainEntity": {
        "@type": "Question",
        "name": "Is this product compatible with other brands?",
        "text": "I would like to know if this product works with equipment from other manufacturers",
        "answerCount": 2,
        "upvoteCount": 15,
        "dateCreated": "2024-01-10T14:30:00+00:00",
        "author": {
            "@type": "Person",
            "name": "Customer"
        },
        "acceptedAnswer": {
            "@type": "Answer",
            "text": "Yes, this product is designed to be compatible with most standard equipment from major brands. It uses universal connectors and follows industry standards.",
            "dateCreated": "2024-01-10T16:00:00+00:00",
            "upvoteCount": 25,
            "author": {
                "@type": "Person",
                "name": "Expert Support Team"
            }
        }
    }
}
```

## Example output

Rendered by the module on the home page of the example store.
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@context": "https://schema.org/",
    "@type": "QAPage",
    "mainEntity": {
        "@type": "Question",
        "name": "Is this product compatible with other brands?",
        "text": "I would like to know if this product works with equipment from other manufacturers",
        "answerCount": 2,
        "upvoteCount": 15,
        "dateCreated": "2024-01-10T14:30:00+00:00",
        "author": {
            "@type": "Person",
            "name": "Customer"
        },
        "acceptedAnswer": {
            "@type": "Answer",
            "text": "Yes, this product is designed to be compatible with most standard equipment from major brands. It uses universal connectors and follows industry standards.",
            "dateCreated": "2024-01-10T16:00:00+00:00",
            "upvoteCount": 25,
            "author": {
                "@type": "Person",
                "name": "Expert Support Team"
            }
        }
    }
}
```

## Good to know

- For pages where shoppers answer a question, such as a product Q&A. For a list of your own questions and answers, use **faq-page**.

_A demo template: its values are examples, not data from your store._
