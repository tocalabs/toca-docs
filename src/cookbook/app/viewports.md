# Making Your App Responsive (See Your App Through A Different Lens)

When building your app pages, one of the important things to focus on is how your app will look on different devices. For example, if your building a store front, on laptop you might want your product filters on the side, whereas on mobile, due to the reduced horizontal space, you will wont the filters to be above the product lists.

In Toca, we handle this with the idea of viewports.

## What are Viewports?
Viewports are used for customising how an app looks across different screen sizes. There are 5 different viewports that you can customise:

- **Widescreen**
  Default Screen Width: 2160px
- **Desktop (default)**
  Default Screen Width: 1440px
- **Laptop**
  Default Screen Width: 1280px
- **Tablet**
  Default Screen Width: 768px
- **Mobile**
  Default Screen Width: 414px

![[Pasted image 20250912103621.png]]

When you first create an app, there are default widths that are automatically set for each viewport. This can be adjusted, from the settings. 

Go to **Theme > Viewport Breakpoints**
![[fig1.png]]
*Fig 1. Viewport Settings*

**Viewport Breakpoints**
In this section, you will see the option to set viewport widths for your different screens.

**Viewport Mode**
There are two modes:
- **Snap to Layout**
  In this mode, the width of your components will be restricted to never exceed the nearest viewports. 
- **Fluid Layout**
  In this mode, the width of your components will allow your components to span the width of the entire window.


## Editing Viewports

![[fig2.png]]
*Fig 2. App Designer - Desktop*

When you enter an app page, by default, the 'Desktop' viewport is selected. This can be seen in the viewports bar and viewports drop down in *Fig 2.*

> *Quick Tip:* Start building your pages for your target viewport first. This way you can can complete you main design and then overwrite the other viewports to fit.

You will notice that when you make changes to a viewport, those changes will automatically reflected in all other viewports (see *Fig 3.*). This lets you develop the features for your app without needing to rebuild it for all viewports.

<figure>
	<p align="center">
		<img src="fig3_1.png" width="48%">
		<img src="fig3_2.png" width="48%">
	</p>
</figure>
*Fig 3. Changes across viewports*

### Switching Between Viewports
To switch between viewports, you have few options available.

**Viewports Bar**
![[fig4a.gif]]
*Fig 4a. Navigation using viewports bar.*

The viewports bar provides a representation of the widths that the different viewports take up. Simply click on one of the sections, and your viewport wil be switched.

**Viewports List**
![[fig4b.png]]
*Fig 4b. Navigation using viewports dropdown.*

**Resizing Canvas**
![[fig4c.gif]]
*Fig 4c. Navigation by resizing.*
### Visibility

![[fig5.png]]
*Fig 5. Visibility Toggle*

You won't always want to have all your components in all your viewports. For example, you might have a specific feature that you want users to have in desktop / laptop which you don't want them to have in mobile.

To handle this, every component comes with a visibility toggle (see *Fig 5.*). This toggle lets you choose whether the selected component is visible in a specific viewport. After toggling this off, you will see the component disappear from your current viewport, but if you switch to another component.

![[fig6a.png]]
*Fig 6a. Visibility Icon in Explorer Tab*

![[fig6b.png]]
*Fig 6b. Visibility Menu*

Alternatively, if we take a look in the explorer tab (right side of window, see *Fig 1.*), hovering over the component icon reveals an visibility button. On clicking this button, a menu will appear that lets you set the visibility for all work items at once.

> **Note**
> When you hide parent component (component with components inside), any components inside will also become hidden. Revealing the parent component, will return the child components to their individual visibilities.

---
Now that we know how to modify our different viewports to display only the relevant components, there may also be instances where you would like to show the same components in two viewports, but lay them out differently, or change some of the content or wording. This can be done with something called ===Responsive Overrides===. 
### Responsive Overrides

![[fig7a.png]]
*Fig 7a. App in Desktop Viewport*

Let's take a look at this using an example. Feel free to follow along.

In an app (see *Fig 7a.*), we have a Flex Layout with a horizontal flow, and within it two other *Flex Layouts*, one with a 33% width (Filters) and another with a 66% width (Products).

```
Root
└─ Flex Layout
   │  [ Flow: Horizontal ]
   │  [ Minimum Height: Full Page ]
   ├─ Filter
   │  │  [ Width: 33.33% ]
   └─ Products
      │  [ Width: 66.66% ]
```

If we switch over to the 'Mobile' viewport, we can see that in this view, the components look very crammed (see *Fig. 7b)*.

![[fig7b.png]]
*Fig 7b. App in Mobile Viewport (No overrides)*

To fix this, we could switch the flow of the parent *Flex Layout* to 'Vertical'. However, if we do this now, it will set the flow to vertical across all viewport.

So, before we make our change to a component, we should first enable the overrides for this section. To do this, click the override button (which looks like a line through devices, see *Fig 5.*), and after reading the message presented in the confirmation box, press 'Yes' if you wish to continue.

![[fig7c.png]]
*Fig 7c. Component properties after enabling overrides*

Once the overrides have been enabled, we can now modify that component, without worrying about it affecting other viewports.

![[fig7d.gif]]
*Fig 7d. Viewports after overrides and modifications*

After all your modifications have been complete, and you switch between your viewports, you will notice that all your viewports have their own design (see *Fig 7d*).

### Orphaned Components
![[Pasted image 20250912154047.png]]

