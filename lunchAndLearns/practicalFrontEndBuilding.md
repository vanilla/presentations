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
brew install node@10
brew link --force --overwrite node@10
sudo rm -r node_modules (if you had node already)
brew install yarn --without-node
composer install
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
--- 

###Stretch Goal: manually run install and manually run build

If you don't know what you can do, look at the `package.json` file!

--- 

#### Manually run:
```
yarn install
yarn build
```

--- 

###Stretch Goal: "hot" reloading

Have your files compiles dyamically as you change them! Note that you might need to stop and rerun the hot realod when you have new files.

--- 

#### PHP config:
```php
$Configuration['HotReload']['Enabled'] = true;
```

--- 

#### in your terminal
```
yarn build:dev
```
