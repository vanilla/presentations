# [fit] Plugins 
# [fit] Rule

---

# [fit] ...or is it 
## [fit] **addons**?  
<br />
# Plugins vs:

## ---- Applications 
## ---- Locales
## ---- Themes

^ Applications: deprecated
Locales: giant arrays
Themes: purely semantic difference

---

# [fit] PLUGIN 
# [fit] THEORY

---

# Magic!

We use `__call()` to _hook_, _extend_, and _override_ existing methods. All use this signature:

`{Class}_{Name}_{Action} ($Object, $EventArguments)`

like:

`ProfileController_EventName_Handler($Sender, $Args)` 

---

# Actions

* _Handler
* _Create
* _Override
* _Before & _After (xRender)

Anything extending `GDN_Pluggable` (every Controller and Model). 

_Views are the context of their Controller._

---

# Code Conventions

* $Sender (object), $Args (array)
* Group related hooks vs. helpers
* Keep it _DRY_ for multiple hooks

---

# [fit] Names Matter

* Events - _follow patterns_
* Variables - _max clarity_
* Methods - _min complexity_

`$neverUseJavaProgrammerNames || $c`

---

# [fit] REFERENCE

* Don't reinvent the wheel
* Example & Eventi plugins
* Other plugins that have a similar hook

---

# Let's talk open source

^ Differences between cloud & open source and how to talk to clients who request an open source plugin.

---

^ Plugins to check out

### [fit] Example
### [fit] NoBump / Bump
### [fit] Flair
### [fit] Salesforce

---

# [fit] Sanity Checks

* There's _no precedence_
* _LEGIBILITY_ over micro-optimisations
* Overview & changelog in _class doc_
* Core vs. addons vs. internal

---

# [fit] Weird cases

`Base_` references ALL contexts.

`_Create` receives $Args from URL.

---

# [fit] Virtual 
# [fit] Controllers

Redispatching from `PluginsController_SomeName_Create` to `Controller_Index` etc.

---

# [fit] hooks to know

`Gdn_Dispatcher_AppStartup_Handler`: earliest hook to use typically.

`Base_Render_Before` covers every pageload.

`AssetModel_StyleCss_Handler` to add new CSS files.

`Base_AfterReactions_Handler` adds widgets to end of posts.

`Base_AuthorInfo_Handler` adds info after the name of the poster.

---

### [fit] Sup?