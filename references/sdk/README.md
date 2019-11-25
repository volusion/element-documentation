# ElementSdk Client Reference

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

See [How to Read Page URI Parameters from Your Block](how-to/read-page-uri-parameters-in-blocks/README.md) for more details.

**Tip**: To explore the SDK without even building a block you can navigate to Site Designer or a page built on Element in your browser, and access the methods directly from your javascript console like this:

```js
window.ElementSdk.client.categories.get()
    .then(console.log)
    .catch(console.error);
```

## `client.bag`

## `client.cart`

## `client.categories`

## `client.checkConfiguredOrFail`

## `client.configure`

## `client.contentPages`

## `client.menus`

## `client.payPal`

## `client.products`

## `client.request`

## `client.setStoreInfo`

## `client.storeInfo`

## `client.storeInformation`

## `client.tenant`
