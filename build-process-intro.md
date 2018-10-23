# Building Vanilla
## For Fun & Profit

--- 

## Who is building Vanilla

Anyone running Vanilla >= 2.8 who did not:

- Download it from the Github releases page.
- Download it from our open source forum releases page.

It is pre-built _only_ for those to cases with phing.
If you checkout vanilla from git, it __needs__ to be built.

---

## What is being being built?

- Dependencies are installed (composer + yarn)
- Addon + Smarty template caches cleared (in the future may be build ahead of time)
- Stylesheets (Sass/SCSS -> Autoprefixer -> CSS)
- Scripts (TypeScript -> ES2018 -> ES5)
- Assets (Images/SVGs -> Inlined/Compressed)

--- 

# When are we building?

### Builds are run 2 different ways with different trade offs.

---

## Production Builds

- `yarn build` or `composer install` (run `yarn build` in post-install step).
- Run every time you do composer install.
- Build super optimized, performant assets.
- Runs on deploy to infrastructure (push code || jarvis deploy).
- Builds every addon present.

---

## Dev builds

- `yarn build:dev`
- Run when actively working on new features.
- Optimized for build time, not performance.
- Do not generate real files on disk. Served out of a separate web server.
- Builds only enabled addons (parses your config files).

---

## Why are we building? (Stylesheets)

[Sass](https://www.sassmeister.com/gist/6d2046052abe1a0b18fcca0e880df1fa) & [https://autoprefixer.github.io/](https://autoprefixer.github.io/).

- Code re-usability
  - Variables.
  - Functions.
  - Mixins.
- Browser compatibility (autoprefixer)

---

## Why are we building? (Scripts)

- Module system.
- Type safety (typescript).
- Optimization.
  - Minify/Uglify.
  - Dead code elimination.
- New language features w/ browser compatibility.
  - Polyfills.
  - Transpilation.
  - [Babel REPL](https://babeljs.io/en/repl#?babili=false&browsers=&build=&builtIns=false&spec=false&loose=false&code_lz=MYGwhgzhAEDKD2BbApgYXFaBvAUNaEALmIQJbAHFnAAqAFqQHYDm0AvNIQE4CuyA3Hk4MW7TrwE4AvjhyhIMVAxAATaMgAehZIxUwEKdAuzRpQA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=es2017%2Creact%2Cstage-0%2Cstage-1%2Cstage-2%2Cstage-3%2Cenv&prettier=true&targets=&version=6.26.0&envVersion=1.6.2)

---

## Without Build

__file1.js__

```js
window.myFunction = function myFunction(myVar) {
    return myVar.someProperty
};
```

__file2.js__

```js
// Hope that we included that other script earlier in the page.
// IDE has no idea:
// - this function exists.
// - this call generate an error.
window.myFunction();
```

---

## With Build

__file1.ts__

```ts
export function myFunction(myVar: { someProperty: boolean }): boolean {
    return myVar.someProperty;
}
```

__file2.ts__

```ts
import { myFunction } from "./file1.ts";
myFunction() // Compiler/IDE error!! Missing argument to function call.
```

---

# The Where and How

## A quick overview of the inputs and outputs.

---

## Sections

The Vanilla product has been divided into 3 "section" that each have their scripts build separately.
Because everything is module based they can still shared many of the same source files,
but they are built separately for performance reasons.

- "forum"
- "admin"
- "knowledge"

---

## Source files

A source file is a file that you want to have compiled.

- Files __must__ be in `src/scripts` directory of your addon.
- Files __must__ be TypeScript.
- Entry files are automatically detected in the `src/scripts/entries` directory of your addon.
- Addons are allowed 1 entry file per section. All other imports are done from there.
- Entry files are named according to section. Eg. to add an entry for the "forum" section create `src/scripts/entries/forum.ts`

---

## Aliases

- `@library` -> `/library/src/scripts`
- `@dashboard` -> `/applications/dashboard/src/scripts`
- `@vanilla` -> `/applications/dashboard/src/scripts`
- `@rich-editor` -> `/plugins/rich-editor/src/scripts`
- `@knowledge` -> `/plugins/knowledge/src/scripts`

---

## Example

```ts
import { registerReducer } from "@library/state/reducerRegistry";
import { onReady } from "@library/application";
import "../../scss/editor.scss";

onReady(() => {
    registerReducer("editor", editorReducer);
    void setupEditor();
});

async function setupEditor() {
  const discussionFormContainer = document.querySelectorAll(".richEditor");
  if (discussionFormContainer.length > 0) {
    const mountEditor = await import(
      /* webpackChunkName: "mountEditor" */
      "@rich-editor/mountEditor"
    );
    discussionFormContainer.forEach(mountEditor.default);
  }
}
```

---

## Output files

Build into the top level `/dist` directory.

- `runtime` - webpack specific.
- `vendors`- node_modules.
- `shared` - Common code from `@library`
- `addons/*` - Addon entry points.
- `bootstrap` - Kicks off all other scripts with the by triggering all `onReady()` callbacks.
- `async~` - Dynamic imports.

![right](https://duaw26jehqd4r.cloudfront.net/items/2b0k0j0G2l3g020a0i1R/Image%202018-10-23%20at%2011.39.42%20AM.png?v=6b65cb98)

---

## Loading built files

It's automatic! If your controller extends `Gdn_Controller` or `KnowledgeTwigPageController` (eg. All existing controllers in our product)
the scripts and stylesheets here will be automatically loaded for you if your addon is enabled.

`async~` files are loaded automatically on the frontend.

---

## How to use this for a new addon

1. Create the `src/scripts/entries` directory there.
2. Create an entry for your desired section. Eg. `forum.ts`, `admin.ts`, or `knowledge.ts`.
3. Write your code.
4. ??
5. Profit.

---

## Rules

- Use typescript.
- Respect the [coding standard](https://docs.vanillaforums.com/developer/contributing/coding-standard-typescript/). Its mostly auto-formatted.
- Use the utilities from library. Eg.
  - `@library/dom`, `@library/utility`, `@library/apiv2`, `@library/application`.
  - Various react components in `@library/components`.
- Don't use jQuery.

---

## jQuery alternatives
- [http://youmightnotneedjquery.com/](http://youmightnotneedjquery.com/).
- Use React or normal JS instead.

---

## Easy substitutions
- `jQuery()`/`$()` -> `element.querySelector()`/`element.querySelectorAll()`
- `$.closest()` -> `element.closest()`
- `$.find()` -> `element.querySelector()`/`element.querySelectorAll()`
- `$.contains()` -> `element.contains()`
- `$.on()` -> `element.addEventListener()`
- `$.delegate()` -> `delegateEvent()` from `@library/dom`.
- `$.ajax()` -> [axios](https://github.com/axios/axios)