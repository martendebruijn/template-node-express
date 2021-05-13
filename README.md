# Template Node Express README

# Introduction

Some introduction

# TOC

# Usage

```bash
git clone ...
npm i
npm i -g terser
npm start
npm start:dev
```

# Dependencies

- `compression`- used for...
- `dotenv`- used for...
- `ejs`- used for...
- `express`- used for...
- `node-fetch`- used for...
- `path`- used for...

## DevDependencies

- `autoprefixer`- used for...
- `chokidar`- used for...
- `cssnano`- used for...
- `eslint`- used for...
- `eslint-config-prettier`- used for...
- `nodemon`- used for...
- `postcss`- used for...
- `postcss-cli`- used for...
- `postcss-sorting`- used for...
- `prettier`- used for...
- `stylelint`- used for...
- `stylelint-config-standard`- used for...

## Global dependencies

- `terser` - used for...

# File structure

- `server/` - root folder
  - `modules/` - all JS modules go here
    - `router.js` - JS file with all the routes for Express
  - `public/` - public folder – the root folder for the website
    - `dist/` - dist folder – where all the build files go
    - `manifest.json` - Manifest
    - `sw.js` - ServiceWorker
  - `src/` - source folder – the files we're working on in dev
    - `css/` - folder for all .css files
      - `predence/` - .css files with predence for concatenating (that have to be on top)
        - `reset.css` - use reset.css or normalize.css or use your own and delete the ones you don't use
        - `normalize.css` - use reset.css or normalize.css or use your own and delete the ones you don't use
        - `themes/` - themes folder
          - `light.css`
          - `dark.css`
    - `js/` - folder for all .js files
  - `views/` - all template .ejs files
    - `global/` - all global components
      - `_nav.ejs` - nav component prefixed with an underscore
      - `_footer.ejs` - footer component prefixed with an underscore
    - `home/` - homepage
      - `index.ejs` - index of homepage
    - `some-page/` - folder for a page
      - `index.ejs` - the index file for the page
      - `_some-component.ejs` - a component prefixed with an underscore
  - `app.js` - starting point for node
- `.eslintrc.js` - eslint configuration
- `.gitignore` - gitignore
- `.prettierignore` - prettierignore
- `.prettierrc.json` - prettier configuration
- `.stylelintrc.json` - stylelint configuration
- `LICENSE` - license
- `README.md` - readme
- `package-lock.json` - package-lock
- `package.json` - package
- `postcss.config.js` - postcss configuration

# NPM Scripts Overview

- `start` - starts the app
- `start:dev` - starts the app in development mode
- `prettier` - formats all files that aren't in `.prettierignore`
- `lint:es` - lints all .js files
- `lint:css` - lints all .css files
- `lint` - lints all .js _and_ .css files
- `build:es` - builds .es files
- `build:css` - builds .css files
- `build` - builds all .es _and_ .css files
- `watch:es` - to be made
- `watch:css` - to be made
- `watch` - to be made

## prettier

```bash
npm run prettier
npx prettier --write .
```

### VSC extension

some info about the VSC extension

### .prettierignore

### .prettierrc.json

### Prettier and ESLint

## lint:es

```bash
npm run lint:es
npx eslint server/src/js/*.js
```

### .eslintrc.js

## lint:css

```bash
npm run lint:css
npx stylelint server/src/css/*.js
```

### .stylelintrc.json

## lint

```bash
npm run lint
npm run lint:es && npm run lint:css
```

## build:es

```bash
npm run build:es
npm run lint:es && cat server/src/js/*.js > server/public/dist/all.js && terser server/public/dist/all.js -o server/public/dist/all.js
```

### lint

See [lint:es](#lint:es)

```bash
npm run lint:es
```

### concatenating

```bash
cat server/src/js/*.js > server/public/dist/all.js
```

### terser

```bash
terser server/public/dist/all.js -o server/public/dist/all.js
```

## build:css

```bash
npm run build:css
npm run lint:css && cat server/src/css/predence/reset.css server/src/css/*.css > server/public/dist/all.css && npx postcss server/public/dist/all.css -o server/public/dist/all.css
```

### lint

See lint:css

```bash
npm run lint:css
```

### concatenating

```bash
cat server/src/css/predence/reset.css server/src/css/*.css > server/public/dist/all.css
```

### autoprefixer

### sort

### nanocss

All above:

```bash
npx postcss server/public/dist/all.css -o server/public/dist/all.css
```

## build

```bash
npm run build
npm run build:es && npm run build:css
```

## watch:es

```bash
# to be made
```

## watch:css

```bash
# to be made
```

## watch

```bash
# to be made
```
