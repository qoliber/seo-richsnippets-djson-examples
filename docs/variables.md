# Variables

Every value a Rich Snippets template can use, with the page where it has a value and an example from the [example store](../README.md#about-the-example-output). The editor's **Variables & Snippets** panel lists the same variables, so you can insert them with a click.

How a value is inserted (whole value or inside text, and what happens when it is missing) is described in [djson-syntax.md](djson-syntax.md#variables).

## Product: `product.*`

On product pages.

| Variable | Value | Example |
|---|---|---|
| `{{product.name}}` | name | `Cruise Dual Analog Watch` |
| `{{product.sku}}` | SKU | `24-MG05` |
| `{{product.url}}`, `{{product.productUrl}}` | product URL | `https://www.example.com/cruise-dual-analog-watch.html` |
| `{{product.image}}` | base image URL; the first gallery image when there is no base image | `https://www.example.com/media/catalog/product/cache/…/mg05-br-0.jpg` |
| `{{product.shortDescription}}` | short description as plain text | `Whether you're traveling…` |
| `{{product.price}}` | regular price, as the page shows it | `55` |
| `{{product.finalPrice}}` | final price, as the page shows it | `55` |
| `{{product.currency}}` | storefront currency | `USD` |
| `{{product.reviewCount}}` | number of approved reviews | `4` |
| `{{product.ratingValue}}` | average approved rating, 1–5; empty without votes | `3.3` |
| `{{product.ratingSummary}}` | the same average, 1–5 | `3.3` |
| `{{product.typeId}}` | product type | `simple` |
| `{{product.isSimple}}`, `{{product.isConfigurable}}`, `{{product.isBundle}}`, `{{product.isGrouped}}`, `{{product.isComplexProduct}}` | `1` or `0` | `1` |
| `{{product.hasTierPrices}}` | `1` when the product has volume (tier) prices | `0` |
| `{{product.stock.availability}}` | schema.org availability URL | `https://schema.org/InStock` |
| `{{product.stock.isInStock}}` | `1` or `0` | `1` |
| `{{product.stock.qty}}` | quantity | `100` |

**Any product attribute** is available by its code, in camelCase or snake_case: `{{product.urlKey}}` and `{{product.url_key}}` both give `cruise-dual-analog-watch`. For dropdown and multiple-select attributes you get the option label: `{{product.activity}}` gives `Recreation`, not an option ID.

## The offer: `commerce.offer`

On product pages. The single Offer the page makes, at the price it shows, with the store's tax display and currency.

| Variable | Value | Example |
|---|---|---|
| `{{commerce.offer}}` | the whole Offer object | see below |
| `{{commerce.offer.url}}` | offer URL | `https://www.example.com/cruise-dual-analog-watch.html` |
| `{{commerce.offer.price}}` | price | `55` |
| `{{commerce.offer.priceCurrency}}` | currency | `USD` |
| `{{commerce.offer.availability}}` | schema.org availability URL | `https://schema.org/InStock` |

```json
{
    "@type": "Offer",
    "url": "https://www.example.com/cruise-dual-analog-watch.html",
    "price": 55,
    "priceCurrency": "USD",
    "availability": "https://schema.org/InStock"
}
```

| Product type | `commerce.offer` |
|---|---|
| Simple, virtual, downloadable | one unit |
| Bundle | the cheapest purchasable configuration, at the "As low as" / "From" price; empty when the bundle cannot be bought |
| Configurable | the lowest price of its in-stock variants (of all variants when none is in stock); `InStock` when any variant is |
| Grouped | empty |

Use `"@djson if commerce.offer"` to publish an offer only when there is one.

## Variants: `variantGroup`, `productVariants`

On configurable product pages, when at least one variant attribute is mapped under **Configurable Variant Attributes**.

| Variable | Value |
|---|---|
| `{{variantGroup}}` | the whole ProductGroup: `@id`, `name`, `url`, `productGroupID`, `variesBy` and `hasVariant` |
| `productVariants` | the list of variants, for a loop. Each has `@type`, `@id`, `name`, `sku`, `url`, `offers`, `image` and the mapped properties (`color`, `size`, `material`, `pattern`) |

See the [product-group](../snippets/product-pages/product-group/) example.

## Shipping and return policies: `merchant.*`

On every page, once configured under **Stores → Configuration → Qoliber → SEO: Rich Snippets → Merchant Shipping and Returns**. Empty until then.

| Variable | Value |
|---|---|
| `{{merchant.shippingDetails}}` | an OfferShippingDetails object: rate and destination |
| `{{merchant.returnPolicy}}` | a MerchantReturnPolicy object: country, category, days, method and fees |

Use them as whole values. Their fields cannot be read one by one.

## Category: `category.*`

On category pages.

| Variable | Value | Example |
|---|---|---|
| `{{category.id}}` | ID | `4` |
| `{{category.name}}` | name | `Bags` |
| `{{category.url}}` | URL | `https://www.example.com/gear/bags.html` |
| `{{category.urlKey}}` | URL key | `bags` |
| `{{category.image}}` | image URL | |
| `{{category.description}}` | description as plain text | |
| `{{category.metaTitle}}` | meta title | |
| `{{category.metaDescription}}` | meta description | |
| `{{category.productCount}}` | number of products | `14` |

## Configuration: `config.*`

On every page. Any store configuration value, by its path with dots instead of slashes, read for the current store view: `{{config.general.store_information.name}}` reads `general/store_information/name`.

The editor lists the common ones:

| Group | Variables |
|---|---|
| Store Information | `config.general.store_information.name`, `.phone`, `.hours`, `.price_range`, `.street_line1`, `.street_line2`, `.city`, `.postcode`, `.region_id`, `.country_id`, `.merchant_vat_number` |
| Locale | `config.general.locale.code` (`en_US`), `.timezone`, `.weight_unit`, `.firstday`, `.weekend` |
| Currency | `config.currency.options.base`, `.default`, `.allow` |
| Base URLs | `config.web.secure.base_url`, `.base_link_url`, `.base_media_url`, `.base_static_url`, and the same under `config.web.unsecure` |

The general contact email is `{{config.trans_email.ident_general.email}}`.

## Store: `store.*`

On every page.

| Variable | Value | Example |
|---|---|---|
| `{{store.name}}` | store view name | `Default Store View` |
| `{{store.code}}` | store view code | `default` |
| `{{store.baseUrl}}` | the store view's base URL | `https://www.example.com/` |
| `{{store.secureBaseUrl}}` | secure base URL | `https://www.example.com/` |
| `{{store.currencyCode}}`, `{{store.currentCurrency.code}}` | storefront currency | `USD` |

For your company name, use `{{config.general.store_information.name}}`. `store.name` is the store view's name.

## System: `system.*`

On every page.

| Variable | Example |
|---|---|
| `{{system.currentDate}}` | `2026-11-20` |
| `{{system.currentDateTime}}` | `2026-11-20T10:38:43` |
| `{{system.currentYear}}` | `2026` |
| `{{system.storeId}}` | `1` |
| `{{system.websiteId}}` | `1` |

## schema.org values: `enum.*`

On every page. The schema.org URLs, so you do not have to type them.

| Variable | Value |
|---|---|
| `{{enum.itemCondition.NewCondition}}`, `.UsedCondition`, `.RefurbishedCondition`, `.DamagedCondition` | `https://schema.org/NewCondition` … |
| `{{enum.availability.InStock}}`, `.OutOfStock`, `.PreOrder`, `.Discontinued`, `.LimitedAvailability` | `https://schema.org/InStock` … |
| `{{enum.priceValidUntil}}` | 31 December of the current year, `2026-12-31` |

## Lists for loops

Use them with `"@djson for list as item"`. Inside the loop, `{{item.field}}` reads the current entry.

| List | On | Fields of each entry |
|---|---|---|
| `breadcrumbs` | every page; the full trail on category and product pages | `position`, `label`, `link` (the last crumb links to the current page) |
| `products` | category pages | `position`, `name`, `productUrl` |
| `productReviews` | product pages | `nickname`, `title`, `detail`, `createdAt`, `rating` (1–5, empty without a vote), `reviewId` |
| `productTierPrices` | product pages with volume prices | `qtyMin`, `qtyMax` (absent on the last row), `price`, `priceExclTax` |
| `productVariants` | configurable pages | see [Variants](#variants-variantgroup-productvariants) |

`productTierPrices` starts with the one-unit price, then one row per tier. On the example configurable product: `{"qtyMin": "1", "price": "22"}`, `{"qtyMin": "10", "price": "15"}`.

## Other snippets: `snippet.*`

`"{{snippet.identifier}}"` pastes in another active snippet by its identifier. See [how snippets work](how-snippets-work.md#1-includes).

## Without a value in Rich Snippets 2.6.2

A few names appear in shipped templates or in the editor but have no data in this version. Replace them with fixed values, or leave them out:

| Name | Where it appears | Renders |
|---|---|---|
| `page.title`, `page.description`, `page.url` | **webpage** | `null` |
| `store.description` | **local-business** | `null` |
| `storeHours` | **store** | an empty list |
| `productGallery` | editor panel | an empty list |
