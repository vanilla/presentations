footer: © 2017 Vanilla Forums
slidenumbers: true

# [fit] Translations for CSMs
___

# [fit] How it works?

---

# [fit] Building translations

Vanilla has a "Dictionary" of translations. It will build up the final "Dictionary" by loading a series of definitions:

## PHP Example:
`$Definition['Add Category'] = 'Ajouter une catégorie';`

---

## Locale config example:
```
{
    "Add Category": "Ajouter une catégorie"
}
```

---

## Vanilla Loads the  translations in the following order:

- Core (i.e. transifex translations)
- Theme
- Plugin
- Config

*The same key can be redefined multipls times. The last loaded definition is the one used.*

---

## [fit] Looking up a definition

**Translations can be loaded either in PHP** 

`t('Some Key')`

**or in Smarty template** 
`{t c="Some Key"}`


*If the definition is not found, the key is used.*

---

# [fit] Troubleshooting

* Typo, very slight variations
* Redefining English strings:
  * `$Definition['Start a New Discussion'] = 'New Discussion';`
  * https://github.com/vanilla/vanilla/blob/master/applications/vanilla/locale/en.php

---

* Client broke translation function in template or is not in a "t" function
* Mobile themes that are proprietary
* Placeholders/variables 
  * Reused for multiple situations
    * "In the category" - >"In <b>%s.</b>"
  * Impossible to have every variant, like user name: `$Definition['EmailHeader'] = 'Hello {User.Name}!`

---

# [fit] Where should they go?

* Transifex -> Vanilla Core, longer term but much slower
* Theme/Plugins -> Faster, easier to track/find, not shared by everyone, so good for client customizations
* Config -> good for quick fixes, but would be better in theme/plugin.
  * Will not work in Lithe or other premade mobile themes
  * Will not work if they have more than one language enabled

---

# How do I find the key?

* https://staff.vanillaforums.com/discussion/121/how-to-find-a-locale-key-in-vanilla
* If you have a hard time finding a string, use a smaller piece, ideally something unique enough to not get hundreds of results.
* Still can't find it? Ask a dev

---

#[fit] Questions?
