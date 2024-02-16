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
Images are standard markdown elements. Images files should be uploaded to this repository and relatively linked.

`![Alt text](/images/someimage.jpg)`