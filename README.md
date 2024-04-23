# Toca documentation
In-platform documentation files for Toca.

Each document should be in it's own file, be named in a URL-safe way (the file will be request via it's filename) and completely self contained (except images). Documents can use all standard markdown syntax, plus the following custom elements:

## Datachips
### Variable chip
Render a variable (eg pink) datachip. Takes a label argument and an optional type property.

`:datachip-variable[label]{type="String"}`

### Action chip
Render an action result (eg green) datachip. Takes a label argument and an optional type property.

`:datachip-action[label]{type="Number"}`

### Datastore chip
Render a datastore (eg blue) datachip. Takes a label argument and an option type property,

`:datachip-datastore[label]{type="Boolean"}`

## Images
Image files should be uploaded to this repository and relatively linked. You can either use the standard markdown image format, or if you need extra control (eg adding width or height attributes) you can use a directive.

* Standard format `![Alt text](src/images/someimage.jpg)`
* Directive `:img{src="/src/images/someimage.jpg" alt="Alt text" width="320px" height="240px"}`

## Linking to other docs
You can link to other docs using the `docs-link` entity. You need to provide an `id` and and optional `type` (if not provided it will assume you want platform documention). For platform documentation the `id` is the filename. See below for which property to use to TDK entities.

Available types are: `Platform` (eg files found in this repo), `Action`, `Connector`, `AppAction`, `AppComponent`.

Link to a platform doc: `:docs-link[Link text]{id="example"}`

### Linking to TDK Entities
To link to a TDK entity you need to provide as the `id` the shared ID property for that type. Below is a list of which property to use.

| Type | Property to use |
| - | - |
| Action | `key` |
| Connector | `connectorId` |
| AppAction | `originId` |
| AppComponent | `originId` |

Linking to the latest version of a TDK action: `:docs-link[Link text]{id="ExecutePython" type="Action"}`

Linking to the latest version of an App action: `:docs-link[Link text]{id="666f4b43-efeb-40da-8f72-05f0d50334bd" type="AppAction"}`

## Videos
You can embed videos into docs using the below syntax. The videos are handled natively, and no conversion or compression is performed so make sure your video files are in a sensible and widely used format (mpeg, webm etc.) and aren't overly large.

```markdown
:video{src="/src/assets/video.mpeg"}
```