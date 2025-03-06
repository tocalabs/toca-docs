# Languages

Multilingual apps use [ISO 639](https://www.iso.org/iso-639-language-code) 2-letter language codes to identify specific languages. [A useful list of these can be found on Wikipedia](https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes). In Toca languages will usually be listed as their name followed by their code eg `English EN`, `Spanish ES` etc. In exported CSV and PO/POT files languages will typically be referenced by just their language code.

## Region modifiers
Region modifiers take the form of a language code followed by a country code eg `en-gb`, `en-us` etc. **Region modifiers are currently not supported by apps**. However, if an app user's browser gives the app a region-modified language code, the app will automatically strip out the region modifier – eg `pt-br` will be treated as `pt`.
