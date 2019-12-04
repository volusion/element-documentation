# What Is Element?

Element is a modern web design and hosting platform. It was designed from the ground up on these guiding principles:

- Incredible speed
- Impeccable SEO
- Amazing developer experience

**Site owners** will enjoy increased conversions due to Element's fast page load times and improved discoverability from our unmatched SEO. **Site visitors** will enjoy consistently fast experiences across all their devices, reducing wait times, frustration, and their tendanancy to bounce. And, **developers** will enjoy an amazingly fluid and straightforward experience designing and deploying their creative ideas.

Read more about how each of these principles benefits the entire ecosystem.

### Speed

We take speed seriously.

- We developed state of the art Server Side Rendering (SSR) technologies to achieve the fastest experiences possible.
- Content is automatically minified, cached, and populated in CDNs for you.
- Our serving technology auto-scaled based on demand, ensuring consistently fast speeds even under heavy, spikey traffic.
- Element is [Google AMP](https://developers.google.com/amp) ready, so you can build your sites to take [advantage of AMP](https://amp.dev/about/how-amp-works/) speed. Developers can progressively add AMP support to your page by making sure you follow some [simple techniques](http://simple-amp-techniques) when developing on Element. But no need to worry, if you don't want to be AMP ready by default your sites will still be [super fast](http://keeping-sites-fast).

### SEO

As the full markup of the site is generated on the server, search engines will get all the content to rank your sites better. Developers have full control over all aspects of SEO custom tags and content.

### Developer friendliness

We give you the full power of Javascript and React. No need to learn a custom programming language or an antiquated templating system. Additionally, we handle for hosting, caching, and CDN delivery for you, so you can focus on building your sites.

## Further Reading

In a nutshell, Element lets you build web applications from small React applications (called Blocks) that can be built separately. Then, you can group them together in pages as you see fit. When a page is requested by a user, all those small Javascript applications that you grouped into a page are rendered in our servers for better concurrency and the fastest markup generation possible. Once the page reaches the browser, the markup is hydrated to apply all the interactivity elements to your site. You can communicate between the page's Blocks by using a simple PubSub mechanism.

To learn more about Element, read the [Concepts](../explanation/element-concepts) explanation.
