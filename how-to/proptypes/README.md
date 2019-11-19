# Add Element Proptypes to a Block

In this how-to guide we will add new Element Proptypes to an existing Element Block React Component and organize them using an Element Proptype `shape`.

## 1. Find the Current Block Configs

Open up your block's code and find `/src/configs.js`. It will look something like this:
```js
export const getConfigSchema = ElementPropTypes => {
    return {
        text: {
            label: 'Text content',
            type: ElementPropTypes.string
        }
    };
};

export const defaultConfig = {
    text: 'Element Starter Block'
};
```

## 2. Add a New Element Proptype

Add another proptype to the schema. You need to provide a label property and a type. For this example we'll add a `color` prop, but look at the [Proptypes Reference](https://github.com/volusion/element-proptypes) for other available types.
```js
export const getConfigSchema = ElementPropTypes => {
    return {
        text: {
            label: 'Text content',
            type: ElementPropTypes.string
        },
        textColor: {
            label: 'Text color',
            type: ElementPropTypes.color
        }
    };
};
```

## 3. Add a New Default Value

Still in `config.js`, when you add a new Element Proptype to a schema, you need to give it a default value:
```js
export const defaultConfig = {
    text: 'Element Starter Block',
    textColor: 'rgba(130,104,252,.8)'
};
```

## 4. Use the New Prop in the Block

We can now use that new proptype in the block. Open `/src/Block.js` and add a style attribute to the `<h1>` tag assigning our new textColor prop to the color.
```html
<h1 style={{color: props.textColor}}>
```

## 5. Add Another Related Element Proptype

Return to `/src/configs.js` and add another prop: `backgroundColor`.
```js
export const getConfigSchema = ElementPropTypes => {
    return {
        text: {
            label: 'Text content',
            type: ElementPropTypes.string
        },
        textColor: {
            label: 'Text color',
            type: ElementPropTypes.color
        },
        backgroundColor: {
            label: 'Background color',
            type: ElementPropTypes.color
        }
    };
};
```

## 6. Organize Proptypes with a Shape

Group the colors together using `ElementPropTypes.shape`:
```js
export const getConfigSchema = ElementPropTypes => {
    return {
        text: {
            label: 'Text content',
            type: ElementPropTypes.string
        },
        colors: {
            label: 'Colors',
            type: ElementPropTypes.shape({
                textColor: {
                    label: 'Text color',
                    type: ElementPropTypes.color
                },
                backgroundColor: {
                    label: 'Background color',
                    type: ElementPropTypes.color
                }
            })
        }
    };
};
```

## 7. Update Config Schema Usage

Restructure the default configs to match the new nesting provided by the shape:
```js
export const defaultConfig = {
    text: 'Element Starter Block',
    colors: {
        textColor: 'rgba(130,104,252,.8)',
        backgroundColor: 'yellow'
    }
};
```
 
Go back into `/src/Block.js` and update the style of the `<h1>` to use our new property and nested structure. Be careful to use `props.colors` not `props.color`.

```html
<h1 style={{color: props.colors.textColor, background: props.colors.backgroundColor}}>
```

## 8. View Your Config in Site Designer

Build and update your block:
```shell
npm run build
element update
```
Add your block to a theme, or reload your theme with the block, and you'll see the new props and default values, grouped under the Colors heading from the shape:

![New Proptypes Colors Shape in Site Designer](newShapeInSiteDesigner.png)
