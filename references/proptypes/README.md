# Visual Guide to Proptypes

## number

![Number: 42](proptype-number.png)

```js
number: {
    label: 'Number',
    type: ElementPropTypes.number
}
```

```js
export const defaultConfig = {
    number: 42,
};
```

## bool

![Boolean: true](proptype-bool.png)

```js
boolean: {
    label: 'Boolean',
    type: ElementPropTypes.bool
}
```

```js
export const defaultConfig = {
    boolean: true,
};
```

## string

![String: Default string](proptype-string.png)

```js
string: {
    label: 'String',
    type: ElementPropTypes.string
}
```

```js
export const defaultConfig = {
    string: 'Default string',
};
```

## color

![Color: purple](proptype-color.png)

```js
color: {
    label: 'Color',
    type: ElementPropTypes.color
}
```

```js
export const defaultConfig = {
    color: 'purple', // all CSS color formats accepted
};
```

## product

![Product](proptype-product.png)

```js
product: {
    label: 'Product',
    type: ElementPropTypes.product
}
```

## category

![Category](proptype-category.png)

```js
category: {
    label: 'Category',
    type: ElementPropTypes.category
}
```

## sectionHeader

![Section Header](proptype-section-header.png)

```js
sectionHeader: {
    type: ElementPropTypes.sectionHeader
}
```

```js
export const defaultConfig = {
    sectionHeader: 'Section Header'
};
```

## image

![Image: empty default](proptype-image.png)

```js
image: {
    label: 'Image',
    type: ElementPropTypes.image
}
```

```js
import { ElementPropTypes } from '@volusion/element-proptypes';

export const defaultConfig = {
    image: ElementPropTypes.image.default
};
```

![Image: Default URL](proptype-image-default.png)

```js
imageWithPlaceholder: {
    label: 'Image With Default',
    type: ElementPropTypes.image
}
```

```js
export const defaultConfig = {
    imageWithPlaceholder: {
        uriBase: 'http://d21ivvgspl06jm.cloudfront.net/',
        imagePath: 'element-block-assets/slideshow/slide2.jpg',
        altText: 'Monument Valley',
        width: 1600,
        height: 500
    }
};
```

![Image Picker](image-picker.png)

## slider

![Slider: default](proptype-slider.png)

```js
sliderDefault: {
    label: 'Slider Default',
    type: ElementPropTypes.slider
}
```

```js
export const defaultConfig = {

};
```

![Slider: options](proptype-slider-options.png)

```js
sliderOptions: {
    label: 'Slider Options',
    type: ElementPropTypes.slider
}
```

```js
import { ElementPropTypes } from '@volusion/element-proptypes';

export const defaultConfig = {
    sliderOptions: {
        labelPrefix: "~",
        labelStepSize: 10,
        labelSuffix: " oz",
        min: 50,
        max: 100,
        stepSize: 5,
        selectedValue: 75,
        vertical: false
    }
};
```

## editorFull

![Editor Full](proptype-editor-full.png)

```js
editorFull: {
    label: 'Editor Full',
    type: ElementPropTypes.editorFull
}
```

```js
export const defaultConfig = {
    editorFull: '<h1>Full WYSIWYG</h1>'
};
```

![Editor Full](editor-full.png)

## editorMinimal

![Editor Minimal](proptype-editor-minimal.png)

```js
editorMinimal: {
    label: 'Editor Minimal',
    type: ElementPropTypes.editorMinimal
}
```

```js
export const defaultConfig = {
    editorMinimal: '<p>Minimal text editor&#8230;</p>'
};
```

![Editor Minimal](editor-minimal.png)

## readOnly

![Read-only](proptype-read-only.png)

```js
readOnly: {
    label: '',
    type: ElementPropTypes.readOnly
}
```

```js
export const defaultConfig = {
    readOnly: 'Read-only text.' // use for instructions, help text
};
```

## oneOf

![oneOf](proptype-one-of.png)

```js
oneOf: {
    label: 'Dropdown',
    type: ElementPropTypes.oneOf(['News', 'Photos'])
}
```

```js
export const defaultConfig = {
    oneOf: 'News'
};
```

## shape

![Shape](proptype-shape.png)

```js
shape: {
    label: 'Shape',
    type: ElementPropTypes.shape({
        text: {
            label: 'Text',
            type: ElementPropTypes.string
        },
        url: {
            label: 'Link',
            type: ElementPropTypes.string
        }
    })
}
```

```js
export const defaultConfig = {
    shape: {
        text: 'Link',
        url: 'https://'
    }
};
```

## arrayOf shape

![arrayOf Shape](proptype-array-of-shape.png)

```js
arrayOfShapes: {
    label: 'Array of Shapes',
    type: ElementPropTypes.arrayOf(
        ElementPropTypes.shape({
            text: {
                label: 'Text',
                type: ElementPropTypes.string
            },
            url: {
                label: 'Link',
                type: ElementPropTypes.string
            }
        })
    )
}
```

```js
export const defaultConfig = {
    arrayOfShapes: []
};

// or pre-populated
export const defaultConfig = {
    arrayOfShapes: [
        {
            text: 'Link',
            url: 'https://'
        }
    ]
};
```

## embeddable

![Embeddable](proptype-embeddable.png)

```js
embeddable: {
    label: 'Embeddable Iframe',
    type: ElementPropTypes.embeddable({
        embedType: ElementPropTypes.string,
        url: ElementPropTypes.string,
        height: ElementPropTypes.number
    })
}
```

```js
export const defaultConfig = {
    embeddable: {
        embedType: 'iframe',
        url: 'https://www.volusion.com/login',
        height: 150
    }
};
```

## Private Properties

The `isPrivate` property set to true hides a field from merchants. Agency accounts will still be able to see it.

```js
string: {
    label: 'String',
    type: ElementPropTypes.string,
    isPrivate: true
}
```

## Further reading

- [Working with Element Proptypes Tutorial](/tutorials/proptypes/README.md)
- [How to: Add Element Proptypes to a Block](/how-to/proptypes/README.md)