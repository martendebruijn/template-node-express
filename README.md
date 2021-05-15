# Template Node Express README

## Introduction

Template for Web app using Node, Express and EJS. With a linter for JavaScript and CSS files, auto-prefixing and sorting CSS. Also supports compression and minifying and PWA setup.

## TOC

- [Usage](#usage)
- [Dependencies](#dependencies)
  - [DevDependencies](#devdependencies)
    - [Linters](#linters)
    - [POSTCSS](#postcss)
- [File structure](#file-structure)
- [NPM scripts](#npm-scripts)
  - [NPM scripts overview](#npm-scripts-overview)
  - [NPM scripts full list](#npm-scripts-full-list)

## Usage

```bash
git clone https://github.com/martendebruijn/template-node-express.git
npm i
npm start
npm start:dev
```

Use either `normalize.css` or `reset.css` or supply your own or neither. Make sure to delete the ones you don't use and update the NPM script `concat:css` accordingly. Make sure to use the latest version if the ones supplied here are outdated.

## Dependencies

- `compression`- used for compressing the application
- `dotenv`- used for handling `.env`
- `ejs`- used for templating
- `express`- used for routing
- `path`- used for `.use(express.static(path.join(__dirname, "public")))` in `app.js`

### DevDependencies

- `nodemon`- auto-restarting server in development mode
- `prettier`- to make files look nice

#### Linters

- `stylelint`- used for linting CSS
- `stylelint-config-standard`- standard configuration for stylelint
- `eslint`- used for linting JavaScript
- `eslint-config-prettier`- configuration to make ESLint and Prettier work nicely togheter

#### POSTCSS

- `postcss`- used for sorting, auto-prefixing, lint and minify CSS
- `postcss-cli`- to use POSTCSS with npm scripts
- `postcss-sorting`- used for sorting CSS
- `autoprefixer`- used for auto-prefixing CSS
- `cssnano`- used for minifying CSS

## File structure

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

## NPM scripts

### NPM scripts overview

- `start` - start app
- `start:dev` - start development mode
- `sort-css` - sort css according to rules
- `prettier` - run prettier on all files except the ones in `.prettierignore`
- `lint:es` - lint all `.js` files
- `lint:css` - lint all `.css` files
- `lint` - lint all `.js` and `.css` files
- `concat:es` - concatenate all `.js` files
- `concat:css` - concatenate all `.css` files
- `concat` - concatenate all `.js` and `.css` files
- `min:es` - minify JavaScipt
- `min:css` - minify CSS
- `minify` - minify JavaScript and CSS
- `prefix-css` - auto-prefix CSS
- `build:es` - build JavaScript
- `build:css` - build CSS
- `build` - build JavaScript and CSS

### NPM scripts full list

#### start

```bash
node server/app.js
```

Starts the application.

#### start:dev

```bash
nodemon server/app.js
```

Starts the application in development mode.

#### sort-css

```bash
postcss -c postcss.config.js --no-map -r server/src/css/global.css
```

Sorts CSS according to the rules declared inside `postcss.config.js`.

```js
module.exports = (ctx) => ({
  plugins: {
    'postcss-sorting': {
      order: [
        'custom-properties',
        'dollar-variables',
        'declarations',
        'at-rules',
        'rules',
      ],

      'properties-order': 'alphabetical',

      'unspecified-properties-position': 'bottom',
    },
  },
});
```

#### prettier

```bash
prettier --write .
```

##### Configuration

`.prettierrc.json`

```json
{
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5"
}
```

- `singleQuote` - use single quotes
- `tabWidth` - 2 (= default) it's just there to let devs see that I use this setting
- `trailingComma` - `es5` (= default) it's just there to let devs see that I use this setting

#### lint:es

```bash
eslint server/src/js/.
```

Lint all `.js` files inside `server/src/js`.

##### Configuration

The configuration file `.eslintrc.js` is located in the root folder. I haven't really looked at the configuration/ESlint rules (yet).

This template also uses Prettier and to make them work nicely together, you have to install [eslint-config-prettier](<[https://github.com/prettier/eslint-config-prettier](https://github.com/prettier/eslint-config-prettier)>) via `npm i -D eslint-config-prettier` . Also add `'prettier'` to the ESLint configuration file (as the last one!):

```js
module.exports = {
  env: {
    browser: true,
    es2021: true,
  },
  extends: ['eslint:recommended', 'prettier'],
  parserOptions: {
    ecmaVersion: 12,
    sourceType: 'module',
  },
  rules: {
    quotes: ['error', 'single'],
  },
};
```

- `quotes` - use single quotes

##### --fix

If the linter displays `x error and y warnings potentially fixable with the '--fix' option`, you can use:

```bash
  npx eslint path/to/file.js --fix
```

##### Configuration

The configuration file `.eslintrc.js` is located in the root folder. I haven't really looked at the configuration/ESlint rules (yet).

This template also uses Prettier and to make them work nicely together, you have to install [eslint-config-prettier](<[https://github.com/prettier/eslint-config-prettier](https://github.com/prettier/eslint-config-prettier)>) via `npm i -D eslint-config-prettier` . Also add `'prettier'` to the ESLint configuration file (as the last one!):

```jsx
module.exports = {
  env: {
    browser: true,
    es2021: true,
  },
  extends: ['eslint:recommended', 'prettier'],
  parserOptions: {
    ecmaVersion: 12,
    sourceType: 'module',
  },
  rules: {},
};
```

#### lint:css

```bash
npm run prefix-css && stylelint server/src/css/.
```

Before linting run auto-prefix script, that way you'll also check those.

Lint all `.css` files inside `server/src/css/.`. Except for `reset.css` or `normalize.css` (`.stylelintignore`) and if you want other files you define in `.stylelintignore`.

##### Configuration

The configuration file `.stylelintrc.json` is located in the root folder. I've installed `stylelint-config-standard` ( `npm i -D stylelint-config-standard` ):

```json
{
  "extends": "stylelint-config-standard",
  "rules": {
    "font-family-name-quotes": "always-where-recommended",
    "selector-attribute-quotes": "never",
    "string-quotes": ["double", { "avoidEscape": true }],
    "at-rule-no-vendor-prefix": true,
    "media-feature-name-no-vendor-prefix": true,
    "property-no-vendor-prefix": true,
    "selector-no-vendor-prefix": true,
    "value-no-vendor-prefix": true,
    "color-named": "never",
    "color-no-hex": true,
    "declaration-no-important": true
  }
}
```

- `extends` - extends `stylelint-config-standard`
- `font-family-name-quotes` - Expect quotes only when quotes are _recommended_ = font family names that contain white space, digits, or punctuation characters other than hyphens
- `selector-attribute-quotes` - never use selector attribute quotes `[target="_blank"]` → `[target=_blank]`
- `string-quotes` - use double quotes but allow strings to use single-quotes so long as the string contains a quote that would have to be escaped otherwise.
- With usage of `autoprefixer` the following vendor prefixes are disallowed:
  - `at-rule-no-vendor-prefix`
  - `media-feature-name-no-vendor-prefix`
  - `property-no-vendor-prefix`
  - `selector-no-vendor-prefix`
  - `value-no-vendor-prefix`
- `color-named` - Never use named colors
- `color-no-hex` - Don't use hex colors, use `hsl()` as much as possible because it's the easiest to precisely change.
- `declaration-no-important` - Don't use `!important`

#### lint

```bash
npm run lint:es && npm run lint:css
```

Executes the linter scripts for both the JavaScript and the CSS files.

#### concat:es

```bash
cat $(find server/src/js -name '*.js') > server/public/dist/all.js
```

Concatenate all `.js` files inside `server/src/js/*` (including subfolders) and output it in `server/public/dist/all.js`.

#### concat:css

```bash
cat server/src/css/predence/reset.css $(find server/src/css/predence/ -name '*.css' ! -name 'reset.css') $(find server/src/css -path server/src/css/predence -prune -false -o -name '*.css') > server/public/dist/all.css
```

Concatenate all `.css` files. Every CSS file that is put in `server/src/css/predence/*.css` have predence over the 'normal' CSS files and will be on the top of the file. If the order matters, like with `reset.css` or `normalize.css` put the files, in order, at the front of the script **and** exclude them from the `find` command. That way they won't be concatenated twice. For example:

```jsx
cat server/src/css/predence/reset.css server/src/css/predence/important-script.css $(find server/src/css/predence/ -name '*.css' ! -name 'reset.css' ! -name 'important-script.css') $(find server/src/css -path server/src/css/predence -prune -false -o -name '*.css') > server/public/dist/all.css
```

Output file: `server/public/dist/all.css`.

#### concat

```bash
npm run concat:es && npm run concat:css
```

Concatenate all `.js` and `.css` files from `server/src`

#### min:es

```bash
terser server/public/dist/all.js -o server/public/dist/all.js
```

Minify `all.js`. Run this after concatenating (or just run `build:es`).

#### min:css

```bash
postcss server/src/css/global.css --use cssnano > server/public/dist/global.css
```

Minify `all.css`. Run this after concatenating and prefixing (or just run `build:css`).

#### minify

```bash
npm run min:es && npm run min:css
```

Minify `all.js` and `all.css`.

#### prefix-css

```bash
postcss $(find server/src/css -name '*.css') --use autoprefixer -r
```

Auto-prefix CSS, specify the browser needs in `package.json` with the `browserlist` key, for example:

```json
{
  "browserslist": "last 2 versions, iOS >= 8"
}
```

#### build:es

```bash
npm run lint:es && npm run concat:es && npm run min:es
```

Build script for JavaScript files:

1. Linter
2. Concatenating
3. Minifying

#### build:css

```bash
npm run lint:css && npm run prefix-css && npm run concat:css && npm run min:css
```

Build script for CSS files:

1. Linter
2. Concatenating
3. Minifying

#### build

```bash
npm run build:es && npm run build:css
```

Build both JavaScript and CSS files.
