# All the Tech You Need to Know to Develop on Element

This section is really short as you don't need much in order to develop on the Element platform.

## React

We use [React](https://reactjs.org/) as the main framework. We don't use state management packages (like Redux or Mobx), and 
you won't need it but you can add it if you want. Our sites use simple components with local state each. For component communication, we use a simple 
[PubSub](../../how-to/communicate-between-blocks/README.md) mechanism.

## CSS

For CSS, we use `css-in-js` that plays nicely with React. You can read [here](../../how-to/style-a-block-with-aphrodite/README.md) how to use
this technique to styles your components.

## Element CLI

In order to interact with Element, we developed a [CLI](../../how-to/env-setup) for making your workflow easier.

## SDK

When coding, you might need to access `e-commerce` data and other goodies. Each block will have access to an [SDK](../../references/sdk) that will help you 
getting things done in your blocks.

## AMP (optional)

The Element platform is [AMP](https://amp.dev/documentation/) ready. We provide some tools to keep your site AMP compliant. This is optional but recommended
to get all the AMP benefits.
