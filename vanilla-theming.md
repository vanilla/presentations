# Theming in Vanilla

## Repos

* vanilla-clients (https://github.com/vanillaforums/vanilla-clients) vs client repos (https://github.com/vanillaforums)
* symlink theme and possibly plugin
  * Clear your cache

## Baisic Theme Setup

*Bittersweet's a good example*

* Simple folder structure:
  * /design/custom.css
  * /js/custom.js
  * /views/default.master.tpl
    * Smarty https://www.smarty.net/
  * addon.json
  * screentshot.png
* default master assets
  * `{asset name="Content"}`
  * `{asset name="Panel"}`
  * `{debug}`

### Basic Options

* Layout Page
* Branding Page

## Advanced Theme Setup

* Build Scripts
  * Vanilla CLI's your friend: https://github.com/vanilla/vanilla-cli

## Views

* Dashboard's layout page
* Overwriting views
* Customize Theme
  - CSS vs HTML behaviour
* Pockets
  * Custom pocket locations

## Theme hooks

* How to find them

  * Naming convention

* ```php
        public function setup() {
            $this->structure();
        }
    ```

* ```php
        /**
         * Runs on utility/update.
         */
        public function structure() {
            // Set some config settings for a modern layout with top-level categories displayed as headings.
            saveToConfig([
                'Routes.DefaultController' => ['categories', 'Internal'],
                'Vanilla.Categories.Layout' => 'modern',
                'Vanilla.Discussions.Layout' => 'table',
                'Garden.ProfileTabOrder' => ['Discussions', 'Comments', 'Notifications', 'Moderation', 'Inbox', 'Drafts']
            ]);
        }
    ```

* `base_render_before`

  * ```php
           if (inSection('Dashboard')) {
               return;
           }
       ```

  * ```
    $sender->setData("key", "value");
    ```

## Locales

* Custom Locales folder (theme or plugin)
* Locales through console

## Mobile

* Mobile themes
  * Assets from Branding Page
  * Doesn't load desktop locales

## Other Notes

* styles.css

* Theme visibility

* VIP deploys

* styles-compat
