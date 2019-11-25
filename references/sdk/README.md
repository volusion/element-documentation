# Volusion API ElementSdk Client Reference

This document looks at the ways that you can use `window.ElementSdk.client` to call the Volusion API.

## Calling the Sdk

In production block code, the most common place that you'll be using the SDK is in `getDataProps.js`

```js
export const getDataProps = (utils, { productSlug }) => {
    return utils.client.products
        .getBySlug(productSlug)
        .then(product => { product })
        .catch(() => {});
};
```

See [How to Read Page URI Parameters from Your Block](how-to/read-page-uri-parameters-in-blocks/README.md) for more background behind that example.

**Tip**: To explore the SDK without even building a block you can navigate to Site Designer or a page built on Element in your browser, and access the methods directly from your javascript console like this:

```js
window.ElementSdk.client.categories.get()
    .then(console.log)
    .catch(console.error);
```

## `ElementSdk.client` Methods and Properties

### Table of Contents

* [bag](#bag)
* [cart](#cart)
* [Categories](#Categories)
  * `get()`
* [checkConfiguredOrFail](#checkConfiguredOrFail)
* [configure](#configure)
* [contentPages](#contentPages)
* [menus](#menus)
* [payPal](#payPal)
* [Products](#Products)
  * [`products.getById()`](#products.getById())
* [request](#request)
* [setStoreInfo](#setStoreInfo)
* [Store Information](#Store)
  * `storeInfo()`
  * `storeInformation`
* [tenant](#tenant)

### `bag`

### `cart`

### Categories

#### `categories.get()`

A method that returns a Promise that resolves with an array of the configured store's categories.

#### Usage

```js
utils.client.categories.get()
```

#### Response

```js
[
    {
        "contentPageId": "",
        "descriptions": {
            "short": "",
            "long": "",
            "extended": ""
        },
        "id": "123",
        "images": [],
        "name": "Category 1",
        "productCount": 5,
        "seo": {
            "title": "",
            "metaDescription": "",
            "friendlyName": ""
        },
        "state": "Active",
        "subCategories": []
    }, {
        "contentPageId": "",
        "descriptions": {
            "short": "",
            "long": "",
            "extended": ""
        },
        "id": "456",
        "images": [],
        "name": "Category 2",
        "productCount": 3,
        "seo": {
            "title": "",
            "metaDescription": "",
            "friendlyName": ""
        },
        "state": "Active",
        "subCategories": []
    }
]
```

### `checkConfiguredOrFail`

### `configure`

### `contentPages`

### `menus`

### `payPal`

### Products

#### `products.getById()`

A method that returns a Promise that resolves with the data for the given product ID.

#### Usage

```js
utils.client.products.getById()
```

#### Response

```js
{
    "availability": {},
    "categoryIds": [],
    "id": "",
    "images": [],
    "listPrice": 1,
    "name": "",
    "price": 1,
    "productVariants": [{
        "id": "",
        "images": [],
        "isInventoryTracked": false,
        "price": 1,
        "quantity": 0,
        "sku": "",
        "variants": []
    }],
    "relatedProductIds": [],
    "seo_friendlyName": "",
    "seo_metaDescription": "",
    "seo_title": "",
    "sku": "",
    "variantOptions": []
}
```

### `request`

### `setStoreInfo`

### Store Information

#### `storeInfo()`

#### `storeInformation`

A property with an object value containing details about the configured store.

#### Usage

```js
utils.client.storeInformation
```

#### Response

```js
{
    "acceptsStripeAsPayment": false,
    "launched": false,
    "name": "Test Store",
    "seo": {
        "metaDescription": "",
        "metaTitle": "",
        "platformMetaTags": {
            "google": ""
        }
    },
    "socialNetworks": {
        "instagram": ""
    },
    "storeUrl": "",
    "tenant": "",
    "thirdPartyIntegrations": {
        "addThisEnabled": false
    },
    "applePay": {
        "isEnabled": false
    },
    "paypal": {
        "isEnabled": false,
        "primaryEmailConfirmed": false
    },
    "logo": {
        "imagePath": "",
        "uriBase": ""
    }
}
```

### `tenant`

A property with a string value containing the configured store's tenant ID.

#### Usage

```js
utils.client.tenant
```

#### Response

```js
"58533e0d3b77c800172ca14e"
```
