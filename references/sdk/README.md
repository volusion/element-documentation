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

**Tip**: To explore the SDK locally from a block's `local/index.js` file, or from your browser's javascript console from a store running on Element, try this:

```js
window.ElementSdk.client.categories.get()
    .then(console.log)
    .catch(console.error);
```

## `ElementSdk.client` Methods and Properties

### Table of Contents

* [Categories](#categories)
  * [`categories.get()`](#categoriesget)
* [Content Pages](#content-pages)
  * [`contentPages.getBySeoFriendlyName()`](#contentPagesgetbyseofriendlyname)
* [Menus](#menus)
  * [`menus.get()`](#menusget)
* [Products](#products)
  * [`products.getById()`](#productsgetbyid)
  * [`products.getBySlug()`](#productsgetbyslug)
  * [`products.getRelatedById()`](#productsgetrelatedbyid)
  * [`products.getRelatedBySlug()`](#productsgetrelatedbyslug)
  * [`products.getByCategoryId()`](#productsgetbycategoryid)
  * [`products.getWithChildCategories()`](#productsgetwithchildcategories)
* [Request](#request)
* [Store Information](#store-information)
  * [`storeInfo.get()` & `setStoreInfo()`](#storeinfoget--setstoreinfo)
  * [`storeInformation`](#storeinformation)
* [Tenant ID](#tenant-id)
  * [`tenant`](#tenant)

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

### Content Pages

Older stores have pages outside of Element. Manage them from [Volusion Admin Pages](https://admin.volusion.com/pages/list).

#### `contentPages.getBySeoFriendlyName()`

A method that returns a Promise that resolves with the data for the given Content Page SEO Friendly Name (slug).

#### Usage

```js
utils.client.contentPages.getBySeoFriendlyName('page-name')
```

#### Response

```js
{
    "content": "<p>HTML Page</p>",
    "createdOn": "", // iso date string
    "id": "",
    "name": "Page Name",
    "seo": {
        "friendlyName": "page-name",
        "metaDescription": "",
        "modifier": 0,
        "title": ""
    },
    "updatedOn": "" // iso date string
}
```

### Menus

#### `menus.get()`

A method that returns a Promise that resolves with an object with an `items` property that contains array of the configured store's menus. **Note:** the Volusion Admin interface only supports a single menu at this time.

#### Usage

```js
utils.client.menus.get()
```

#### Response

```js
{
    "items": [{
        "createdOn": "",  // iso date string
        "id": "",
        "items": [{
            "id": "",
            "items": [],
            "name": "",
            "slug": "",
            "type": "" // types include 'category', 'product', 'page', 'elementPage', and 'link'
        }, {
            "id": "",
            "items": [],
            "name": "",
            "slug": "",
            "type": ""
        }],
        "updatedOn": "" // iso date string
    }]
}
```

### Products

#### `products.getById()`

A method that returns a Promise that resolves with the data for the given Product ID.

#### Usage

```js
utils.client.products.getById('product123')
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

#### `products.getBySlug()`

A method that returns a Promise that resolves with the data for the given Product SEO Friendly Name (slug).

#### Usage

```js
utils.client.products.getBySlug('product-name')
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

#### `products.getRelatedById()`

A method that returns a Promise that resolves with an array of related products for the given Product ID.

#### Usage

```js
utils.client.products.getRelatedById('product123')
```

#### Response

```js
[
    {
        "id": "",
        "images": [],
        "listPrice": 1,
        "name": "",
        "productVariants": [{
            "id": "",
            "isInventoryTracked": false,
            "price": 1,
            "quantity": 0
        }],
        "salePrice": null,
        "seo_friendlyName": ""
    }, {
        "id": "",
        "images": [],
        "listPrice": 1,
        "name": "",
        "productVariants": [{
            "id": "",
            "isInventoryTracked": false,
            "price": 1,
            "quantity": 0
        }],
        "salePrice": null,
        "seo_friendlyName": ""
    }
]
```

#### `products.getRelatedBySlug()`

A method that returns a Promise that resolves with an array of related products for the given Product SEO Friendly Name (slug).

#### Usage

```js
utils.client.products.getRelatedBySlug('product-name')
```

#### Response

```js
[
    {
        "id": "",
        "images": [],
        "listPrice": 1,
        "name": "",
        "productVariants": [{
            "id": "",
            "isInventoryTracked": false,
            "price": 1,
            "quantity": 0
        }],
        "salePrice": null,
        "seo_friendlyName": ""
    }, {
        "id": "",
        "images": [],
        "listPrice": 1,
        "name": "",
        "productVariants": [{
            "id": "",
            "isInventoryTracked": false,
            "price": 1,
            "quantity": 0
        }],
        "salePrice": null,
        "seo_friendlyName": ""
    }
]
```

#### `products.getByCategoryId()`

A method that returns a Promise that resolves with an array of related products for the given category ID.

#### Usage

```js
utils.client.products.getByCategoryId({ categoryId: 'category123' })
```

#### Advanced Usage

```js
utils.client.products.getByCategoryId({
    categoryId: 'category123',
    page: 1, // one based
    pageSize: 20,
    sort: 'name a-z' // See Product Sort Options at the bottom of this document.
})
```

#### Response

```js
[
     {
        "availability": {
            "preOrder": {
                "enabled": false
            }
        },
        "categoryIds": ["category123"],
        "description": "",
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
    }, {
        "availability": {
            "preOrder": {
                "enabled": false
            }
        },
        "categoryIds": ["category123"],
        "description": "",
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
]
```

#### `products.getWithChildCategories()`

A synchronous method that returns an array with the given category and any subcategories it might have, if passed a category ID and the store's entire category tree (the response from [`categories.get()`](#categoriesget)).

#### Usage

```js
utils.client.products.getWithChildCategories('category123', categoryTree)
```

#### Response

```js
[
    'category123',
    'category123-subcategory'
]
```

### Request

An asynchronous function that behaves exactly like [fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API), returning a promise that resolves with a response from a third party API endpoint.

#### Usage

```js
utils.client.request("https://jsonplaceholder.typicode.com/posts")
    .then(res => res.json())
    .catch(e => []);
```

**TIP:** always use this when [calling third party services](/how-to/data-third-party-services) so that your block behaves consistently when rendered by the server or on the client-side.

### Store Information

#### `storeInfo.get()` & `setStoreInfo()`

A method that returns a Promise that resolves with the data for the configured store's tenant, and a method to set that data on the `storeInformation` property.

#### Usage

```js
utils.client.storeInfo
    .get()
    .then(data => {
        utils.client.setStoreInfo(data);
    });
```

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

### Tenant ID

#### `tenant`

A property with a string value containing the configured store's tenant ID.

#### Usage

```js
utils.client.tenant
```

#### Response

```js
"58533e0d3b77c800172ca14e"
```

## Additional Notes

### Product Sort Options

* `"lowest price"`
* `"highest price"`
* `"newest"`
* `"name z-a"`
* `"name a-z"`
