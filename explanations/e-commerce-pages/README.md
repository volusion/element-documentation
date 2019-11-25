# E-commerce Theme Pages

Site Designer is part of the Element platform. Element is a generic website building tool, but Site Designer is more than a generic site builder. As a companion to the e-commerce platform Volusion, when you create a new theme in Site Designer it comes pre-loaded with pages that display e-commerce related content, such as products and categories.

In this discussion we will examine each of the pre-built e-commerce related pages that come with a Site Designer theme, learn about their settings, and take a look at their component blocks.

## Options When Creating a New Theme

If you want a head start with the fonts and colors, visit the Theme Gallery and choose a pre-designed theme. If you create a new theme from the link on "My Themes" the design will be simpler, but it will have all the same e-commerce pages.

## Home Page

Your home page will start out empty if you are creating a theme from scratch, or pre-populated with some blocks if you chose a theme from the gallery. What all themes start out with in common is a header and a footer block as part of their global template.

If you want to learn more about working with your template, read [How to Add Blocks across All Your Site Pages Using Templates](/how-to/add-blocks-to-templates/README.md). What we will look at here is what content the header and footer blocks display, and where it comes from.

### Header

The header will either shore your store's name, or your logo. Add your logo in [Settings > Store Information](https://admin.volusion.com/settings/detail).

The header also includes your menu, which you can change using the [Menu Editor](https://admin.volusion.com/editstore/menu). The menu may behave differently on mobile devices than on larger displays.

### Footer

The footer may contain a set of links. Those links are suggestions, the pages do not exist yet. You may want to [add those pages to your theme](/how-to/add-page-to-theme/README.md), and then edit your footer block so that it links to those pages. Otherwise remove the links to any pages that don't exist.

An address appears in the footer by default, along with email and phone number. You should edit those from the footer block.

You may see some social media icons in the footer. If not, add them in the Social Media Accounts at the bottom of [Settings > Store Information](https://admin.volusion.com/settings/detail).

At the bottom in small text there is a copyright notice. Change the company name by editing the block.

## Product Details

Products are the core of any e-commerce site. This page will be easier to work with if you have created at least one product from the Volusion admin. Ideally you would have at least two, and set them up as related to each other.

### Page Settings

Here are the settings that are available when you click the settings icon in the page dropdown across from "Product Details". You do not need to alter any of these fields:

1. If you have an Agency account you can delete this page, but then you will have to re-create it.
2. The Page Title will be the product name, this value is not used.
3. The Page Path is useful as a reference. If you have an Agency account you can edit the path, but that will remove it from the Site Map, so this is not recommended.
4. As with the Page Title, the SEO field values will come from the individual products. Edit the product in Volusion admin to set these values for your product.

### Product Details Block

**Tip:** the Product Details block will not load in Site Designer if your store has no products.

You will be able to re-arrange the product data a bit, moving the image to the left or right, and deciding where the description should go. Display options for when you have more than one image appear here.

If you have an Agency account you may specify which product is displayed. This is not useful here where the URL determines the product. It would be used for displaying details of a specific project on a separate page if you wanted to do that. For example, you could build a stand-alone landing page with a slideshow and an article all about one product, and then include the Product Details block on that page.

### Related Products Block

A couple notes for Agency accounts:

1. Do not change the Product directory path field unless you have changed the Page Path above in Page Settings, which you should not have done.
2. The Get related products field is not needed on this page. It will get products related to the current product. Where that field is useful is for including the Related Products block on another page, such as your home page.

## Search Results

This page will show a grid of product search results. As with Product Details above, there is no need to change any of the page settings. Editing the Page Path could result in it needlessly appearing in your site map.

### Search Results Block

Here you will find column and color controls. Again, Agency accounts should leave the Product directory field alone.

## Category

The settings for the Category page load dynamically from the Volusion Admin categories.

### Category Page Block

Do not select a category from the category field. The category field is for embedding the category block in another page where the URL does not dynamically select a category. If you select one here, each of your category page URLs will show the same category.

For Agency accounts, no need to edit the Product directory path field.
