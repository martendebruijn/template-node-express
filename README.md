# Template Node Express README

# Introduction

Some introduction

# TOC

# Usage

```bash
git clone ...
npm i
npm start
npm start:dev
```

# Dependencies

- `compression`- used for...
- `dotenv`- used for...
- `ejs`- used for...
- `express`- used for...
- `path`- used for...

## DevDependencies

- `nodemon`- used for...
- `prettier`- used for...

### Linters

- `stylelint`- used for...
- `stylelint-config-standard`- used for...
- `eslint`- used for...
- `eslint-config-prettier`- used for...

### POSTCSS

- `postcss`- used for...
- `postcss-cli`- used for...
- `postcss-sorting`- used for...
- `autoprefixer`- used for...
- `cssnano`- used for...

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

# NPM Scripts

## Overview

- `start`
- `start:dev`
- `sort-css`
- `prettier`
- `lint:es`
- `lint:css`
- `lint`
- `concat:es`
- `concat:css`
- `concat`
- `min:es`
- `min:css`
- `minify`
- `prefix-css`
- `build:es`
- `build:css`
- `build`

## start

```bash
node server/app.js
```

## start:dev

```bash
nodemon server/app.js
```

## sort-css

```bash
postcss -c postcss.config.js --no-map -r server/src/css/global.css
```

## prettier

```bash
prettier --write .
```

## lint:es

```bash
eslint server/src/js/.
```

Lint all `.js` files inside `server/src/js`.

### Configuration

The configuration file `.eslintrc.js` is located in the root folder. I haven't really looked at the configuration/ESlint rules (yet).

This template also uses Prettier and to make them work nicely together, you have to install [eslint-config-prettier](<[https://github.com/prettier/eslint-config-prettier](https://github.com/prettier/eslint-config-prettier)>) via `npm i -D eslint-config-prettier` . Also add `'prettier'` to the ESLint configuration file (as the last one!):

```jsx
module.exports = {
  env: {
    browser: true,
    es2021: true,
  },
  extends: ["eslint:recommended", "prettier"],
  parserOptions: {
    ecmaVersion: 12,
    sourceType: "module",
  },
  rules: {},
};
```

## lint:css

```bash
stylelint server/src/css/.
```

Lint all `.css` files inside `server/src/css/.`. Except for `reset.css` or `normalize.css` and if you want other files you define in `.stylelintignore`.

### Configuration

The configuration file `.stylelintrc.json` is located in the root folder. I've installed `stylelint-config-standard` ( `npm i -D stylelint-config-standard` ):

```json
{
  "extends": "stylelint-config-standard"
}
```

## lint

```bash
npm run lint:es && npm run lint:css
```

Executes the linter scripts for both the JavaScript and the CSS files.

## concat:es

```bash
cat $(find server/src/js -name '*.js') > server/public/dist/all.js
```

Concatenate all `.js` files inside `server/src/js/*` (including subfolders) and output it in `server/public/dist/all.js`.

## concat:css

```bash
cat server/src/css/predence/reset.css $(find server/src/css/predence/ -name '*.css' ! -name 'reset.css') $(find server/src/css -path server/src/css/predence -prune -false -o -name '*.css') > server/public/dist/all.css
```

Concatenate all `.css` files. Every CSS file that is put in `server/src/css/predence/*.css` have predence over the 'normal' CSS files and will be on the top of the file. If the order matters, like with `reset.css` or `normalize.css` put the files, in order, at the front of the script **and** exclude them from the `find` command. That way they won't be concatenated twice. For example:

```jsx
cat server/src/css/predence/reset.css server/src/css/predence/important-script.css $(find server/src/css/predence/ -name '*.css' ! -name 'reset.css' ! -name 'important-script.css') $(find server/src/css -path server/src/css/predence -prune -false -o -name '*.css') > server/public/dist/all.css
```

Output file: `server/public/dist/all.css`.

## concat

```bash
npm run concat:es && npm run concat:css
```

Concatenate all `.js` and `.css` files from `server/src`

## min:es

```bash
terser server/public/dist/all.js -o server/public/dist/all.js
```

Minify `all.js`. Run this after concatenating (or just run `build:es`).

## min:css

```bash
postcss server/src/css/global.css --use cssnano > server/public/dist/global.css
```

Minify `all.css`. Run this after concatenating and prefixing (or just run `build:css`).

## minify

```bash
npm run min:es && npm run min:css
```

Minify `all.js` and `all.css`.

## prefix-css

```bash
postcss server/src/css/global.css --use autoprefixer -d server/src/src/global.css
```

Auto-prefix CSS, specify the browser needs in `package.json` with the `browserlist` key, for example:

```json
{
  "browserslist": "last 2 versions, iOS >= 8"
}
```

## build:es

```bash
npm run lint:es && npm run concat:es && npm run min:es
```

Build script for JavaScript files:

1. Linter
2. Concatenating
3. Minifying

## build:css

```bash
npm run lint:css && npm run prefix-css && npm run concat:css && npm run min:css
```

Build script for CSS files:

1. Linter
2. Concatenating
3. Minifying

## build

```bash
npm run build:es && npm run build:css
```

Build both JavaScript and CSS files.
