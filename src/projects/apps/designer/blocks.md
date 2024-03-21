# Blocks

Blocks are preconfigured and styled components that you can use to build consistent content across your app :docs-link[pages]{id="projects/apps/pages"}. These blocks may include layouts, buttons, text, nav bars, cards, and other components that are commonly used in apps. Using blocks can help you save time and maintain consistency across your app.

By using blocks of components in apps, you can speed up the design and development process and ensure consistency and coherence across different pages.

You can create as many blocks as you need in an app, but you can only use them inside that app. If you wish to group together a set of components to form a layout which you can use across multiple apps then you should look at :docs-link[Layouts]{id="projects/apps/designer/layouts"}.

If you want to update one of the components from a block, this will also update everywhere where it is used in the project. Also, if you delete the block from the menu, it will be deleted from everywhere where it is used.

In order to make Blocks a bit more flexible, you can configure Blocks to accept one or more _inputs_. These inputs allow you to make Blocks more generic and then drive them with data which can be defined in each place that you drag your Block into your App.

## Blocks vs Layouts

Blocks and :docs-link[Layouts]{id="projects/apps/designer/layouts"} are conceptually similar but are meant to be used in different scenarios. First, let's cover the key differences:

1. Blocks are specific to a single App, you cannot use a Block from one App in another App
2. Blocks are not editable unless you "unlink" the block once you have placed it down, once unlinked you cannot relink it to the original block
3. Block content is static with the exception of the block's inputs
4. Layouts are built in the TDK rather than from within an App
5. Layouts will place the individual components on your app page when it is dragged in, a Block will place the Block down as if it is a single component
6. Layouts will typically contain generic content which will need changing once you have placed a Layout onto your App page. A Block's content is usually static and will not require changing

With the above differences in mind, Blocks are best placed for generating common static blocks of content such as a navbar or a footer that is common across mulitple pages in your App. Layouts are much better for applying design templates or scaffolding your app page so that you can build faster but they still require some configuration such as populating the content within the layout.
