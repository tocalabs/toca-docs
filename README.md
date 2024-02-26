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
Images files should be uploaded to this repository and relatively linked. You can either use the standard markdown image format, or if you need extra control (eg adding width or height attributes) you can use a directive.

* Standard format `![Alt text](src/images/someimage.jpg)`
* Directive `:img{src="/src/images/someimage.jpg" alt="Alt text" width="320px" height="240px"}`

## Linking to other docs
You can link to other docs using the `docs-link` entity. You need to provide an `id` and and optional `type` (if not provided it will assume you want platform documention). For platform documentation the `id` is the filename. For TDK entities the id will be the `definitionId` or `actionId`.

Available types are: `platform` (eg files found in this repo), `action`, `connector`, `appaction`, `appcomponent`.

Link to a platform doc: `:docs-link[Link text]{id="example"}`

Link to a tdk entity doc: `docs-link[Link text]{id="666f4b43-efeb-40da-8f72-05f0d50334bd" type="appcomponent"}`