# HowTo (DEMO)

Step-by-step instructions.

| | |
|---|---|
| Identifier | `howto` |
| schema.org type | [HowTo](https://schema.org/HowTo) |
| Shown on by default | nowhere until you choose: no page type |
| Includes | — |
| Included by | — |
| After install | inactive |

## What it publishes

A demo guide with total time and three steps.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
{
    "@context": "https://schema.org/",
    "@type": "HowTo",
    "name": "How to Set Up Your New Product",
    "description": "Step-by-step guide to setting up and configuring your new purchase",
    "image": "{{config.web.secure.base_url}}media/howto/setup-guide.jpg",
    "totalTime": "PT15M",
    "step": [
        {
            "@type": "HowToStep",
            "name": "Unpack the product",
            "text": "Carefully remove the product from its packaging and check all components are included",
            "position": 1
        },
        {
            "@type": "HowToStep",
            "name": "Connect power",
            "text": "Plug the power cable into the device and connect to a power outlet",
            "position": 2
        },
        {
            "@type": "HowToStep",
            "name": "Initial configuration",
            "text": "Follow the on-screen instructions to complete the initial setup",
            "position": 3
        }
    ]
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
    "@type": "HowTo",
    "name": "How to Set Up Your New Product",
    "description": "Step-by-step guide to setting up and configuring your new purchase",
    "image": "https://www.example.com/media/howto/setup-guide.jpg",
    "totalTime": "PT15M",
    "step": [
        {
            "@type": "HowToStep",
            "name": "Unpack the product",
            "text": "Carefully remove the product from its packaging and check all components are included",
            "position": 1
        },
        {
            "@type": "HowToStep",
            "name": "Connect power",
            "text": "Plug the power cable into the device and connect to a power outlet",
            "position": 2
        },
        {
            "@type": "HowToStep",
            "name": "Initial configuration",
            "text": "Follow the on-screen instructions to complete the initial setup",
            "position": 3
        }
    ]
}
```

## Good to know

- Google no longer shows HowTo rich results. The markup is still valid structured data.

_A demo template: its values are examples, not data from your store._
