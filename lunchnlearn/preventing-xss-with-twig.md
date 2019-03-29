# Preventing XSS by using twig templates

---

## What is twig?

Twig is a PHP templating engine. It is fast, flexible and maintained by the Symphony project.

---

## Why use Twig

- Simple.
- Secure defaults (prevents XSS).
- Straightforward flow of data.

---

## How do I use it?

- `Vanilla\Web\TwigRenderTrait`
- Default view handling.

---

## TwigRenderTrait

```php
class MyClass {

    use Vanilla\Web\TwigRenderTrait;

    public function myFunction() {
        $data = [
            "title": "Hello World",
            "description": "This is the description.",
            "nested": [
                "property": "I'm nested",
            ],
        ];
        $html = $this->renderTwig("/plugins/my-plugin/view/my-view.twig", $data);
        // Return or echo
        return $html;
    }
}
```

---

## TwigRenderTrait (cont.)

- Path is the full path to root of the Vanilla installation. View could live anywhere.
- No override system in place.
- Data passed is an array. Anything can be passed here. Objects, simple values, callables.

---

## The template

**plugins/my-plugin/view/my-view.twig"**

```html
<div class="container">
    <h3>{{ title }}</h3>
    <p>{{ description }} <span>{{ nested.property }}</span></p>
</div>
```

---

## Dynamic View Lookups

`Gdn_Controller` has a method of automatically looking up views and rendering them. Example

```php
class TestController extends Gdn_Controller {
    public function endpoint() {
        $this->setData('title', 'Hello world');
        $this->setData('description', 'Hello description.');
        $this->render();
    }
}
```

---

## Dynamic View Lookups (cont.)

The following files will be looked up through the addon system.

- `views/test/endpoint.tpl` (Smarty)
- `views/test/endpoint.twig` (Twig)
- `views/test/endpoint.php` (PHP)

The data used will be the controllers `$this->Data` where available.

---

## {{ }}

- Evaluates the expression inside.
- Renders it into the output.

Example
```
{{ nested.into.the.functioncall() }}
```

---

## Property Access

- `.` is used instead of `[]` or `->` this means you don't have to worry if something is an array or object.
- Use ?? if some value may not be defined.

Example
```
{{ deeply.nested.value ?? "Default" }}
```

---

## {% %}

These are for control flow. They will not output any contents.

```html
<div>
    {% if someValue === true %}
        <span />
    {% endif %}

    {% for user in users %}
        {{ user }}
    {% endfor %}
</div>
```

---

## {{- -}}

- The `-` character will strip whitespace before the beginning or end of the expression to the last tag.
- Optional
- Can make for nicer outputted HTML.

---

## Functions available

- [All twig built-ins](https://twig.symfony.com/doc/2.x/)
- [Our built ins](https://github.com/vanilla/vanilla/blob/master/library/Vanilla/Web/TwigRenderTrait.php)
  - `t()` - For making URLs
  - `url()` - For making vanilla URLs
  - `sanitizeUrl()` for sanitizing possibly dangerous URLs.
- Any callables that you explicitly pass in.

---

## Example 1 - New default master

- New default master
  - [View](https://github.com/vanilla/vanilla/blob/master/resources/views/default-master.twig)
  - [Data](https://github.com/vanilla/vanilla/blob/ccbcaceb7343d3ce9986d9ed5127fe9eeaf7a327/library/Vanilla/Web/Page.php#L133-L153)

---

## Example 2 - KB dashboard pages

- Knowledge Base List
  - [View](https://github.com/vanilla/knowledge/blob/master/plugins/knowledge/views/knowledgesettings/index.twig)
  - [Data](https://github.com/vanilla/knowledge/blob/9746dbcdbbbfffb47c0525b2600b8fe89d08ca9d/plugins/knowledge/Controllers/KnowledgeSettingsController.php#L184-L238)
- KB add/edit form
  - [View](https://github.com/vanilla/knowledge/blob/master/plugins/knowledge/views/knowledgesettings/addedit.twig)
  - [Data](https://github.com/vanilla/knowledge/blob/master/plugins/knowledge/Controllers/KnowledgeSettingsController.php#L149-L150)

---

## Summary

- Whenever fixing XSS, try to convert to a twig view, or partially to a twig view.
- All new views should be in twig or react.
