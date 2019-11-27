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

* [Bag](#bag)
  * [`bag.create()`](#bagcreate)
* [Cart](#cart)
  * [`cart.get()`](#cartget)
  * [`cart.getForShopper()`](#cartgetforshopper)
  * [`cart.update()`](#cartupdate)
  * [`cart.addContactAndShipping()`](#cartaddcontactandshipping)
  * [`cart.add()`](#cartadd)
  * [`cart.setShopperId()`](#cartsetshopperid)
  * [`cart.getTotalItems()`](#cartgettotalitems)
  * [`cart.addDiscount()`](#cartadddiscount)
  * [`cart.removeDiscount()`](#cartremovediscount)
  * [`cart.getShipToCountries()`](#cartgetshiptocountries)
* [Categories](#categories)
  * [`categories.get()`](#categoriesget)
* [Config](#config)
  * [`configure()`](#configure)
* [Content Pages](#content-pages)
  * [`contentPages.getBySeoFriendlyName()`](#contentPagesgetbyseofriendlyname)
* [Menus](#menus)
  * [`menus.get()`](#menusget)
* [PayPal](#paypal)
* [Products](#products)
  * [`products.getById()`](#productsgetbyid)
  * [`products.getBySlug()`](#productsgetbyslug)
  * [`products.getRelatedById()`](#getrelatedbyid)
  * [`products.getRelatedBySlug()`](#getrelatedbyslug)
  * [`products.getByCategoryId()`](#getbycategoryid)
  * [`products.getWithChildCategories()`](#getwithchildcategories)
* [Store Information](#store-information)
  * [`storeInfo.get()` & `setStoreInfo()`](#storeinfoget--setstoreinfo)
  * [`storeInformation`](#storeinformation)
* [Tenant ID](#tenant-id)
  * [`tenant`](#tenant)

### Bag

#### `bag.create()`

A method that returns a Promise that resolves with a bag, given a Cart ID, and a returnURI. A Bag ID is used to start the checkout process.

#### Usage

```js
utils.client.bag.create(cartId, returnUri)
```

#### Response

```js
{
    id: "";
    tenantId: "";
    cartId: "";
    returnUri: "";
}
```

### Cart

**Note:** for instead of using the SDK to interact directly with the cart, read [How To Interact with the Cart](how-to/interact-with-the-cart/README.md) using pub/sub events.

#### `cart.get()`

Get the cart.

Method returns a Promise that resolves with a cart, given a Cart ID.

#### Usage

```js
utils.client.cart.get(cartId)
```

#### Cart Response

```js
{
    availableShippingMethods: [
        deliveryEstimate: "",
        id: "",
        name: "",
        shippingPrice: 1,
        shippingPriceInCents: 1
    ],
    billingAddress: {},
    contactInfo: {
        email: "",
    };
    discounts: {
        discount: {
            id: "",
            name: "",
            requiresCouponCode: false
        },
        discountAmount: number;
    },
    grandTotal: 1,
    id: "",
    items: [],
    messages: [],
    shippingAddress: [],
    shippingMethod: {
        id: "",
        name: "",
        shippingBand: {
            shippingPrice: 1
        },
        shippingCost: 1
    },
    taxAmount: 1,
    taxRate: 1,
    total: 1,
    totalItems: 1,
    revision: 1
}
```

#### `cart.getForShopper()`

Get the cart associated with a shopper.

Method returns a Promise that resolves with a cart associated with a shopper, given a Cart ID, Shopper ID, and Shopper Token. If Shopper ID and Token are not defined, a copy of the cart is still returned.

#### Usage

```js
utils.client.cart.getForShopper(
    cartId,
    shopperId,
    shopperToken
)
```

#### Response

See [Cart Response](#cartresponse)

#### `cart.update()`

Update the quantity of a product in the cart.

Method returns a Promise that resolves with a cart, given a Cart ID, the new quantity you are setting, and the ID of the variant you are updating.

#### Usage

```js
utils.client.cart.update(
    cartId,
    newQuantity,
    variantId
)
```

#### Response

See [Cart Response](#cartresponse)

#### `cart.addContactAndShipping()`

Add contact information, and optionally add the selected shipping method, to the cart.

Method returns a Promise that resolves with a cart, given a Cart ID, contact information, and optionally a shipping method.

#### Usage

```js
address = {
    address1: "",
    address2: "",
    city: "",
    state: "",
    postalCode: "",
    country: "",
    firstName: "",
    lastName: ""
}

contactInfo = {
    email: "",
    shippingAddress: address,
    billingAddress: address,
    shippingName: "",
    billingName: ""
}

shippingMethod = {
    id: "", // optional
    name: "",
    shippingBand: {
        shippingPrice: 1
    };
    shippingCost: 1 // optional
}

utils.client.cart.addContactAndShipping(
    cartId,
    contactInfo,
    shippingMethod // optional
)
```

#### Response

See [Cart Response](#cartresponse)

#### `cart.add()`

Add a product to the cart.

Method returns a Promise that resolves with a cart, given a Cart ID, Product ID, Product Quantity, and Variant ID

#### Usage

```js
utils.client.cart.add(
    cartId,
    productId,
    quantity,
    variantId
)
```

#### Response

See [Cart Response](#cartresponse)

#### `cart.setShopperId()`

Associates a shopper with a cart.

Method returns a Promise that returns void, given a Cart ID and a Shopper ID.

#### Usage

```js
utils.client.cart.setShopperId(
    cartId,
    shopperId
)
```

#### Response

No response.

#### `cart.getTotalItems()`

Get the number of items in the cart.

Method returns a Promise that resolves with an object that includes total number of items in the cart, given a Cart ID.

#### Usage

```js
utils.client.cart.getTotalItems(
    cartId
)
```

#### Response

```js
{
    totalItems: 1
}
```

#### `cart.addDiscount()`

Add a discount code to the cart.

Method returns a Promise that resolves with a cart, given a Cart ID and Discount Code.

#### Usage

```js
utils.client.cart.addDiscount(
    cartId,
    discountCode
)
```

#### Response

See [Cart Response](#cartresponse)

#### `cart.removeDiscount()`

Remove a discount code from the cart.

A method that returns a Promise that resolves with a cart, given a Cart ID and Discount ID.

#### Usage

```js
utils.client.cart.removeDiscount(
    cartId,
    discountId
)
```

#### Response

See [Cart Response](#cartresponse)

#### `cart.getShipToCountries()`

Get the countries that the store will ship to.

Method returns a Promise that resolves with an array of objects containing country codes that the store will ship to. Depending on the country, the Administrative Areas in the country object may or may not be empty.

#### Usage

```js
utils.client.cart.getShipToCountries()
```

#### Response

```js
[
    {
        administrativeAreas: [
            "AL",
            "AK" // etc.
        ],
        country: "US"
    }
]

```

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

### Config

#### `configure()`

A method that configures the client with the tenantId for the store you wish to work with. Requests following this method call will query the given store.

#### Usage

```js
window.ElementSdk.client.configure({
    tenant: 'tenantId'
});
```

**Note:** when working with blocks this method will already have been called.

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

**Note:** In most cases getting and setting Store Information will have already been done, and you can read the data from the `storeInformation` property below.

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
