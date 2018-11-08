# Lunch(ish) and Learn

---

## Documentation:

https://docs.vanillaforums.com/developer/tools/building-frontend/#prerequisites

---

##Assumptions:

- brew
- PHP/Composer
- local Server
- Git

---

## Goal

`yarn build`

---

## Installation
```
# From your terminal
brew install node@10

# If you already had node, run:
brew link --force --overwrite node@10

# If you have an issue here, Run brew doctor and follow the instructions it gives you.
brew doctor

# If you already had node_modules installed, run:
sudo rm -r node_modules

# From your Vanilla project folder, run:
brew install yarn --without-node
composer install
```

---

#### Manually run:
```
yarn install
yarn build
yarn check-types

```
---

###Manually run install and manually run build

If you don't know what you can do, look at the `package.json` file!

---

### "Hot" reloading

Have your files compiles dyamically as you change them! Note that you might need to stop and rerun the hot realod when you have new files.

---

#### PHP config:
```php
$Configuration['HotReload']['Enabled'] = true;
$Configuration['Debug'] = true;
```
---

#### Terminal:
```
yarn build:dev 

# Or

yarn build:dev --fix
```
---

## Writing some JS

###Modifying existing file

```
/vanilla/applications/dashboard/src/scripts/entries/forum.tsx 
```
---

###Creating new files

```
vanilla/plugins/stubcontent/src/scripts/entries/admin.ts
vanilla/plugins/stubcontent/src/scripts/entries/forum.ts
```


