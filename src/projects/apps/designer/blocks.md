# Blocks

Blocks are preconfigured and styled components that you can use to build the app. These blocks may include layouts, buttons, text, nav bars, cards, and other components that are commonly used in apps. Using blocks can help you save time and maintain consistency across your app.

By using blocks of components in apps, you can speed up the design and development process and ensure consistency and coherence across different parts of the app.

You can create as many blocks as you need in a project, but you can only use them inside that project.

If you want to update one of the components from a block, this will also update everywhere where it is used in the project. Also, if you delete the block from the menu, it will be deleted from everywhere where it is used.

## Blocks vs Layouts

Blocks and :docs-link[Layouts]{id="projects/apps/designer/layouts"} are conceptually similar but are meant to be used in different scenarios. First, let's cover the key differences:

1. Blocks are specific to a single App, you cannot use a Block from one App in another App
2. Blocks are not editable unless you "unlink" the block once you have placed it down, once unlinked you cannot relink it to the original block
3. Block content is static with the exception of the block's inputs

With the above differences in mind, Blocks are best placed for generating common static blocks of content such as a navbar or a footer. Layouts are much better for applying design templates or scaffolding to your app page so that you can build faster but they still require some configuration such as populated the content within the layout.
