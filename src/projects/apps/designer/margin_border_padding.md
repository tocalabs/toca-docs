# Margin & Border & Padding 


**Margin** is the space around a component's border, while **padding** is the space between a component's border and the component's content. Put another way, the margin property controls the space _outside_ the component, and the padding property controls the space _inside_ the component.

-  **Component** - Any component or layout added to a page
- **Padding** - Specifies the area between the content of the component and the components border
- **Border** - A border that goes around the padding and component, the border is usually invisible unless a colour is specified
- **Margin** - Defines the area between the component's border and the components around it


![Box Model](/src/assets/box_model.png)

In web development, this is referred to as the "Box Model", you can learn more about this [here](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model). 


Let's explore **margins** first. Consider the component illustrated below, which has a margin of 10 pixels:
     
![Margin Diagram](/src/assets/margin.png)


This means that there will be at least 10 pixels of space between this component and neighbouring components from the page — the margin “pushes away” its neighbours.

On the other hand, **padding** is located inside the border of a component. The component below has padding of 10px on the left and right sides, and padding of 15px on the top and bottom sides:

![Padding Diagram](/src/assets/padding.png)


In the Properties of the components and layouts, there is the option to increase the Margin and/or the Padding up to 64 px on each side. 

There you can also customise the Border by adding:

- style: The style can be solid, dashed, dotted or double 
- colours: Used to set the color of the four bourder
- width: The width can be set as a specific size (1px, 2px, 4px or 8px)
- corners.: The corners can be set as a specific size (2px, 4px, 6px, 8px or full
