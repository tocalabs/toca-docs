# Padding

**Padding** is the space between the border of a component and the inner content (e.g. text, image, other components etc.). The component below has padding of 10px on the left and right sides, and padding of 15px on the top and bottom sides:

![Padding Diagram](/src/assets/padding.png)

In the properties of the components and layouts, there is the option to increase the :docs-link[margin]{id="projects/apps/designer/margin"} and/or the padding up to 64 units on each side. These units are arbitrary values which are designed to scale appropriately with different viewports.

## CSS
This option allows you to provide any [valid CSS value](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Values_and_units). For example `12px`, `1.5em`, `calc(100vw - 50px)` etc. Numeric values will be treated as pixels.