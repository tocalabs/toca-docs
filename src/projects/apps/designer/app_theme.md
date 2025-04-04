# App Theme Options

You can customize your theme with various options

**Accent Colours** - These primary and secondary colours and referenced in various app components, and are used in numerous places unless you specify otherwise or are using your own custom components. Usually you will want to put your brand's colour as the primary, and an accent colour as the secondary.

**Typography** - These settings allow you to select your fonts for the app, these fonts styles will act as your default throughout the app, though some components like 'Text' allow you to specify different font stylings. Note: Buttons and other coloured elements will usually have their own text colour calculated based on the contrast of the colour of the element (ie. If your primary accent colour is dark red, then your button's text will automatically be white instead of black).

**Background Colours** - Allow you to change the background of the body of your app as well as the background colour of some 'paper' elements.

**Status Colours** - These colours are primarily used for alert/notification bars which may appear in your app, however some components can consume these colours as well.

**Colour Mode** - This is the general colour theme of the app. Setting Automatic will allow the browser to pick up the user's operating system theme and use that.

:docs-link[**Viewport Breakpoints**]{id="projects/apps/viewport_breakpoints"} - Allows you to modify the breakpoints for when the viewport changes.

**Misc Options** - All other options go here, currently this only houses border radius, which is the level of rounding of elements (0px for right angled corners, with higher values providing more rounded corners)