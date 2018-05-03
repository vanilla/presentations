
# [fit] React Training __*week 2*__

---

# [fit] What is __*Typescript*__?!

---

# What is __*Typescript*__?!

Provides optional static typing, classes and interfaces. It's always __*optional*__ and is discarded for production.

__*Official documentation:*__ https://www.typescriptlang.org/

--- 

# Why __*Typescript*__?! 

* Makes JS strongly typed
* Reduces errors
* Change `.js` files to `.ts` to use it!
* For `.jsx` files, change to `.tsx`

--- 

## Compiling all the things in __*Vanilla*__ 

__*Build Tool:*__
https://github.com/vanilla/vanilla-cli

__*Docs:*__ 
https://docs.vanillaforums.com/developer/vanilla-cli

__*Config:*__ 
`$Configuration['HotReload']['Enabled'] = true;`

---

## Compiling all the things in __*Vanilla*__ (continued)

In one __*terminal*__, run the build

__*For Development:*__ `vanilla build --hot`
__*For Production:*__ `vanilla build`

For now we need to manually do the __*production*__ build before pushing to clients. In the future we'll likely have a more advanced solution.

---

## Compiling all the things in __*Vanilla*__ (continued)

In another __*terminal*__, run the tests

`yarn test --watch`

Follow instructions (`a` to run all tests, etc)

(__*Travis*__ will fail if these tests don't pass)
