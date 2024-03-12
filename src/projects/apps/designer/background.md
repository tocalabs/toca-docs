# Background

The Background properties are used to add background effects for components.

From the properties of the component you can select:
- **Upload an image** From your local storage.
- **Pick Datachip**: You can pick an image as a datachip from the Datastore. 
- **Colour**: Sets the background colour of a component.
- **Blend mode**: Sets how an element's background images should blend with each other and with the element's background color.
- **Image Repeat**: Sets if/how a background image will be repeated. This property may have the following values:
 
| Setting | Description |
| --- | --- |
| _Initial_ | Sets this property to its default value. |
| _No Repeat_ | The background image is not repeated. The image will only be shown once. |
| _Repeat_ | The background image is repeated both vertically and horizontally. |
| _Repeat X_: The background image is repeated only horizontally. |
| _Repeat Y_: The background image is repeated only vertically |
| – _Revert_: Lets you 'undo' styles applied to a component, going back to the parent component. |
| _Round_: The background image is repeated and squished or stretched to fill the space (no gaps). |
 | _Space_: The background image is repeated as much as possible without clipping.|

- **Image size**: Specifies the size of the background images. This property may have the following values:

| Setting | Description |
| --- | --- |
| _Auto_ | Default value. The background image is displayed in its original size. |
| _Contain_ | Resize the background image to make sure the image is fully visible. |
| _Cover_ | Resize the background image to cover the entire container, even if it has to stretch the image or cut a little bit off one of the edges. |
| _Inherit_ | Inherits this property from its parent element. |
| _Initial_ | Sets this property to its default value. |
| _Revert_ | Lets you 'undo' styles applied to a component, going back to the parent component. |
  
- **Image position**: Sets the starting position of a background image.

The background of a component affects the entire area covered by that component, including any padding that may be defined. For example, If you set a background colour or image for the button component in an app, it will cover the entire button area, including the padding.
