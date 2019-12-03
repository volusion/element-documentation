# Cart Events

The Element SDK provides topic names for standard cart events. Blocks can subscribe to these topics, as well as publishing to them, using PubSubJS.

For more details on PubSubJS, see the [PubSubJS npm reference](https://www.npmjs.com/package/pubsub-js).

`this.props.events.cart`, available within block component definitions, is defined as follows:

```js
{
    addToCart: "cart.addToCart",
    itemAddedToCart: "cart.itemAddedToCart",
    itemRemovedFromCart: "cart.itemRemovedFromCart",
    openAccountPanel: "cart.openAccountPanel",
    openCart: "cart.openCart",
    updateCartCount: "cart.updateCartCount",
}
```

Subscriptions using these topics should be referenced as properties of `this.props.events.cart`, not as strings. This is because these topic names are provided by Element SDK and could be subject to change. By using the property values from `this.props.events.cart`, you are guaranteed to have a valid topic name. Using the string is not as safe.

For example, use `this.props.events.cart.addToCart`, not `"cart.addToCart"`.

For more information about how to communicate between blocks using PubSubJS, see the guide for [How to Communicate between Two (Or More) Blocks](../how-to/communicate-between-blocks/README.md)
