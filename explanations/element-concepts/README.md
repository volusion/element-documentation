# Element Concepts

This document will describe the basic concepts of the Element platform.

## Blocks

Blocks are the basic unit of Element. They are small Javascript applications built with React. Some characteristics: 

- Self contained (Can be used and developed independently one from the other).
- Composed of markup (React), styles (css-in-js), and data (universal data fetch).
- Communicate with other blocks using a PubSub mechanism.
- Can fetch data from the Volusion API or any external data source.
- Have configurations defined by the developer that the block user can tweak to customize looks and behavior.

Developing a block is a matter of:

- Using the [Element CLI](TODO-link) to get the block boilerplate.
- Defining and [implementing a configuration](../../how-to/proptypes/README.md) (As a Javascript object).
- Selecting and calling the [data sources](TODO-link-fetching-data-fast) that will populate the block with meaningful data.
- Displaying the data and wiring some interactions. (TODO-link)
- Styling the block to look nice. (TODO-link)
- Publishing the block and using it in pages. (TODO-link)

## Pages

Pages are a collection of blocks. Pages are [created](../../how-to/add-page-to-theme/README.md) and customized using the Site Designer.

In a page, you can add as many blocks as you want. You can use Volusion's blocks, or you can use your own. Each block can be
configured differently on each page, or [use the same configuration across all pages](/how-to/reuse-a-block-across-pages/README.md). It all depends on what you want to achieve.

## Themes

Themes are a collection of pages. You can add a header and a footer to all your pages in a single operation for example, set global
styles that are visible to all your pages, preview your work without affecting your site and many more.

Each store has an installed theme that is visible to all your site users. When you perform an edit to your live theme, a draft copy is created
that can be used without affecting your site. You can apply as many changes as needed without fear. Once you are ready, you can promote
your copy to be the installed theme by publishing it. You can have as many themes as you want to test ideas. Each theme has a preview URL to see the progress
online.

## The E-Commerce Theme

Volusion is an e-commerce platform and we provide a [basic theme starter](../e-commerce-pages/README.md) for that purpose. You can still use Element to build any kind of sites, not
just e-commerce. You can create pages to show a blog list and entries, a Q&A page, reviews, a map, a contact form, basically anything you want.
