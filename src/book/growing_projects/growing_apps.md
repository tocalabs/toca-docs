# Growing Apps

As you start to build out your library of apps or perhaps you are building one large app, you'll start to feel the need to reuse designs and blocks of components. You might have company style guidelines which denote how your login page should look or what your navbars and footers should contain, and you want to make these as consistent as possible across all of the apps you build in Toca. This is where :docs-link[layouts]{id="projects/apps/designer/layouts"} and :docs-link[blocks]{id="projects/apps/designer/blocks"} come in!


## Layouts

Layouts act like templates, allowing you to define the structure and look of a set of components. This is useful for designing a set of templates for common interfaces such as a login screen, footers, forms or dashboards. Once you have defined a layout, you can then access it from any App and simply drag it onto any page in the App Designer. You're then free to tweak the layout how you see fit and plug in the data that you need to make it work for your scenario. The theming of your App will also automatically apply to your layout so as you drag it onto the page, you may notice the typography and colours change to match your app.

To create a layout, head over to the Toca Development Kit (TDK) and hit the Create App Layout button. This will take you to a lightweight App designer that allows you to place down your app components and IPL but you can't wire components up to datastores or listeners. This is intentional as layouts are meant to act as templates, allowing you to rapidly structure your page. Once you've developed your layout in the TDK, save it, set it for review and then once approved, you can add the layout to an existing group in the TDK or you can create a new group (groups just define how the layout appears when you're searching for it).

Once this is all done, you can see your new layout in the regular app designer in the layouts tab on the left hand side and you can drag it onto the app page.


## Blocks

Blocks are a bit different from layouts, they are app specific (so you cannot share blocks across apps) and you can use listeners and datastores as data sources. Blocks are designed to make it easy to copy a set of components you have already placed down on your app page for scenarios where you want to repeat this set of components elsewhere on your app. Groups of components that form navbars or footers are commonly turned into blocks as you need the exact same thing between each page and blocks allow you to copy groups of components across any page of your app.

Blocks behave like a single component, in that you drag them onto your screen and then configure inputs to them if they have any inputs defined, but under the hood they might contain many components. To create a block, you can select a component that you have dragged onto the page and you can turn it into a block by pressing the "Create Block" button on the component menu. This will take the component you have selected and everything inside that component and group them together into a single block. Once you have created your block, you can define inputs on it by going to the Inputs tab which appears on the right hand side of the designer.

To place a block down, head to the Blocks tab in the app designer when you are building a page, and then drag the block from the blocks tab onto the page. You can then define the values for any inputs which your block is expecting.
