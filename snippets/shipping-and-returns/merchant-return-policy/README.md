# Merchant Return Policy

Your configured return policy: country, return window, method and who pays.

| | |
|---|---|
| Identifier | `merchant-return-policy` |
| schema.org type | [MerchantReturnPolicy](https://schema.org/MerchantReturnPolicy) |
| Shown on by default | nowhere on its own: included by other templates |
| Includes | — |
| Included by | [`offer`](../../product-pages/offer/), [`offer-shipping-details`](../../product-pages/offer-shipping-details/) |
| After install | inactive |

## What it publishes

The single placeholder `{{merchant.returnPolicy}}`, built from Merchant Shipping and Returns: country, **Return Policy Category** (finite window, unlimited window, or no returns), **Days to Return a Purchase** (finite windows only), **Return Method** and **Who Pays Return Costs**. Fields you leave on *Not configured* are omitted.

## Template

[`template.json`](template.json), exactly as the module installs it:

```json
"{{merchant.returnPolicy}}"
```

## Variables and directives

- `{{merchant.returnPolicy}}`: configured return policy (object).

All variables: [docs/variables.md](../../../docs/variables.md).

## Example output

Rendered by the module on the product page of *Cruise Dual Analog Watch* (simple product, 4 reviews).
[About the examples](../../../README.md#about-the-example-output).

```json
{
    "@type": "MerchantReturnPolicy",
    "applicableCountry": "US",
    "returnPolicyCategory": "https://schema.org/MerchantReturnFiniteReturnWindow",
    "merchantReturnDays": 30,
    "returnMethod": "https://schema.org/ReturnByMail",
    "returnFees": "https://schema.org/FreeReturn"
}
```

## Good to know

- Include-only: **offer** and **offer-shipping-details** include it under `@djson if merchant.returnPolicy`.
- Nothing is published until **Emit Configured Return Policy** is Yes.
