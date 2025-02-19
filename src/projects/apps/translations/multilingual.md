# Multilingual

Apps can be translated into multiple languages, automatically picking the text to use based on a users location or preference. Toca doesn't translate the text for you – instead it provides the tools allowing you to use the translation service of your choice.

## Multilingual in a nutshell
* Translations are stored in translation tables. Your app may have 1 or many tables - if you use the wizard then translation tables will be associated with specific pages or block (otherwise they're just associated with the app).
* Each translation has a unique key (within the table) and a separate text field for each configured language.
* Translations are applied in your app using translation datachips in your app components (or IPL). For example, if you have a :docs-link[Card component]{id="56974164-6da1-4aea-af7b-25a56a8076b3" type="AppComponent"} you would replace the text in the title with a datachip eg :datachip-variable[my_key]{type="String"}.
* Once deployed the app will attempt to identify the user's language (the user's browser will be configured with one). If the language is supported we will automatically serve the correct text. If we don't support that language, we will instead use the app's default language.

## Getting started

To enable multilingual functionality you can either:
* Enable it during app creation OR
* Enable it via the app `Settings` panel

When enabling this functionality you will be asked to configure the following options:
* Pick the languages you want. **You don't have to provide a exhaustive list now, you can change it later** but you do need to pick at least 1 language.
* Pick the default language for the app. This should be the language you have designed (or will design) your app pages in, and will be used as the fallback if we cannot resolve to another language.
* A `translation table` name. Translation tables are where translations will be stored, and we will get you started by creating a table for general translations. Leave blank to skip creating a table.

Once multilingual is enabled, you can get started with translating your app. You can go about this in a few different ways:

### Manually add translations
The simplest way to add _single translations_ to your app is to add them manually. In the top right of the screen you'll see an `ADD TRANSLATION` button. A dialog panel will appear and prompt you to provide the following information:
* The translation table to store the translation in,
* a `key` - a unique identifier (within the selected table) for the translation,
* the text values for your configured languages. **You only need to provide a value for your default language at this stage** - translations for other languages can be left blank and added later.

Once added you can edit you app component, replacing the text with the translation datachip.

### Run the translation wizard
If you have already built your app (or part of it), the _quickest_ way to translate it is via the the translation wizard (accessible via the dropdown button next to the add translation button). The wizard will take you through the following steps:
1. Select which pages and/or blocks you want to run the wizard on.
2. Select which of the identified text snippets to convert into translation chips.
3. Run the update. **We will automatically create the translations and update the pages/blocks.**

You can run the wizard multiple times, and on whichever pages or block you choose. The wizard will ignore component properties that don't contain any text values eg numbers, datachips etc.

> Properties which contain a mix of text and datachips will be split up into separate parts, and the wizard will ignore the parts that are not strings. **You may need to design (or redesign) your app to handle these situations**, as the translation functionality cannot reorder text and datachips depending on language, and character styling may not work as expected.

### Import a `po` or `csv` file
You can import a `po` file (see below for a description of this type of file) or a `csv` file via the dropdown menu on the top right next to the add translation button. This allows you to create many translations at the same time. **The easiest way to get started with either `po` or `csv` files is by using the export option (see below).**

When importing a file new translations will be added by key, existing translations will be overwritten. You will be prompted to confirm where existing translations are being modified.

## Exporting `pot`, `po` and `csv` files
`pot` and `po` files are a [standard way of handling translations in applications](https://www.gnu.org/software/gettext/manual/html_node/PO-Files.html). `csv` is a basic format for tabular data.
* A `po` file (Portable Object) contains 1 or more strings for a single language (when exporting you will need to pick a language). The file will contain all the strings for that language from the selected tables.
* A `pot` file (Portable Object Template) is a template, containing all the strings from the selected tables with the text from your default language, and is intended to be used by a translation service to produce `po` files (which you can them import).
* A `csv` file (Comma Separated Values) is a simple table data format. This `csv` will contain a column for the `key`, each of the selected languages, and the `id` of the translation table. It will contain a row for for every translation in the selected tables.

You can export these files via the dropdown menu next to the add translation button, and you can import `po` and `csv` files via the same menu.

## Remove unused translations
A utility that will examine your app's pages and blocks, and determine if any of the translations in your translation tables are unused. You can select these unused translations to be removed.
