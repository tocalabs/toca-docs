# Typography

These properties cover the font and it's styling used with this component.

### Font Family
Select a set of fonts to use in priority order (ie the first font will be the font that will be used unless it cannot be loaded, in which case the browser will try to use the next and so on). A font is one of the following:
* **Google font**: loaded from the Google fonts library.
* **Custom font**: a font from a file (or files) that you upload. Enter the name of your custom font into the font selector and press `enter`. Then attach the font file(s) (format should be `WOFF` or `WOFF2`) with the appropriate style and weight options and `Submit`. For example a font with `normal`, `italic`, `bold` and `bold italic` will be 4 separate rows.
* **System font**: a font that is expected to be installed on a user's computer. The font selector will suggest some common system fonts (eg `Arial`, `Georgia` etc.), but you can enter your own by typing it's name and pressing `enter`. You will then see the `Upload custom font` dialog box where you should select the `System` tab, and then press `Submit`.
* **Family**: a generic name for a type of font, typically used as the last fallback in a font family. These are suggested by the font selector and are: `serif`, `sans-serif`, `monospace` and `fantasy`.

### Other properties
| Property | Description |
| - | - |
| Colour | The colour of the text. |
| Size | The text size. Should be a valid css value eg `16px`, `1.5em`, `2rem` etc. |
| Weight | The weight (eg boldness) of the text. Valid values are `lighter`, `normal`, `bold` and `bolder`. |
| Line height | The amount of space each row of text takes up. Think of it as the distance between the top of one row of text and the top of the next row. Can be either a specific css dimension (eg `25px`) or a number, which represents a multiple of the text size (eg if your text size is `16px` the a line height of `1.5` would be calculated as `24px`). |
| Letter spacing | Add extra space between characters. Should be a valid css value eg `1px`. |
| Decoration | Add an `underline`, `overline`, `line-through` (eg strikethrough or crossed out) or `none`. |
| Transform | Force the text to be all `uppercase` or `lowercase`, or `capitalize` (eg the first letter of every word is uppercase), or `none`. |

### Inheritance
These properties will sometimes be inherited by child components, and sometimes not. This depends on how the components are built. Components that use the Material UI library (buttons, cards, form elements etc.) will typically not inherit them. Whether inherited or not, the settings will only be visible in the properties of the component they are set on. **If you want all your components to use the same font, text colour or base font size you should set these in the app theme** rather than in component properties.