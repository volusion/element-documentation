# What Is Element?

Element is a modern web platform to deliver the fastest web experiences for mobile and desktop.

As a developer, you will have a set of tools for building web applications in an easy, fast and fun way.

As a user, you will enjoy a performant and fast experience.

## Principles

The Element platform has its foundations on:

- Speed
- SEO
- Developer friendliness

### Speed

We take speed seriously. Using state of the art Server Side Rendering (SSR) technologies, we achieve the fastest experiences possible.

### SEO

As the full markup of the site is generated on the server, search engines will get all the content to rank your sites better.

### Developer friendliness

We give you the full power of Javascript and React. No need to learn a custom programming language or an antiquated templating system. Additionally, we
handle for hosting, caching, and CDN delivery for you, so you can focus on building your sites.

## High Level Architecture

In a nutshell, Element lets you build web applications from small React applications (called Blocks) that can be built separately. Then, you can group them
together in pages as you see fit. When a page is requested by a user, all those small Javascript applications that you grouped into a page are rendered in
our servers for better concurrency and the fastest markup generation possible. Once the page reaches the browser, the markup is hydrated to apply all the 
interactivity elements to your site. You can communicate between the page's Blocks by using a simple PubSub mechanism.

## Further Reading

To learn more about Element, read the [Concepts](../explanation/element-concepts) explanation.
