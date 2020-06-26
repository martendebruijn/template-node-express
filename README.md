# Template NodeJS with Express

<div style="display:flex;">
  <img src="https://img.shields.io/github/license/martendebruijn/template-node-express" />
</div>

## Introduction

Template repo for NodeJS with Express projects.

## TODO:

- [ ] Update package.json and package-lock.json to new project repo

<!-- ![Screenshot applicatie](/readme_img/screenshot-dark.png) -->

## Table of contents

- [Usage](#usage)
<!-- - [Live Demo](#live-demo) -->
- [Dependencies](#dependencies)
- [NPM Scripts](#npm-scripts)
- [Gulp tasks](#gulp-tasks)
  <!-- - [Credits](#credits) -->
  <!-- - [Whishlist](#whishlist) -->
  <!-- - [Sources](#sources) -->

## Usage

### 1. Clone repo & install dependencies

```zsh
git clone https://github.com/martendebruijn/template-node-express.git
cd template-node-express
npm install
```

<!-- ### 2. Create .env file
Create `.env` file in the **root folder**
Request a key [here](https://openweathermap.org/).

```zsh
KEY=<YOUR_KEY>

``` -->

### 2. Run app

**Build app first**

Inside the terminal

```zsh
gulp
```

**Development**

```zsh
npm run dev
```

**Production**

```zsh
npm start
```

Open a browser and go to localHost

```zsh
localhost:3000
```

<!-- ## Live Demo
[Live demo link](https://real-time-web-marten.herokuapp.com/) -->

## Dependencies

| Dependency        | NPM Package Link                                                     |
| ----------------- | -------------------------------------------------------------------- |
| Compression       | [Compression](https://www.npmjs.com/package/compression)             |
| Dotenv            | [Dotenv](https://www.npmjs.com/package/dotenv)                       |
| Ejs               | [Ejs](https://www.npmjs.com/package/ejs)                             |
| Express           | [Express](https://www.npmjs.com/package/express)                     |
| Gulp              | [Gulp](https://www.npmjs.com/package/gulp)                           |
| Gulp autoprefixer | [Gulp autoprefixer](https://www.npmjs.com/package/gulp-autoprefixer) |
| Gulp clean css    | [Gulp clean css](https://www.npmjs.com/package/gulp-clean-css)       |
| Gulp concat       | [Gulp concat](https://www.npmjs.com/package/gulp-concat)             |
| Gulp terser       | [Gulp terser](https://www.npmjs.com/package/gulp-terser-js)          |
| Node fetch        | [Node fetch](https://www.npmjs.com/package/node-fetch)               |
| Path              | [Path](https://www.npmjs.com/package/path)                           |
| Nodemon           | [Nodemon](https://www.npmjs.com/package/nodemon)                     |

## NPM Scripts

| NPM Script         | Task                                    | What it does                        |
| ------------------ | --------------------------------------- | ----------------------------------- |
| `npm run prestart` | `gulp`                                  | Build CSS and ES files before start |
| `npm start`        | `node server/server.js`                 | Start app                           |
| `npm run dev`      | `gulp watch & nodemon server/server.js` | Run app in development mode         |

## Gulp tasks

| Gulp task                  | Task                   |
| -------------------------- | ---------------------- |
| `gulp css`                 | Build CSS files        |
| `gulp es`                  | Build ES files         |
| `gulp watch`               | Watch CSS and ES files |
| `gulp build` **or** `gulp` | Build CSS and ES files |

## Credits

- [Meyerweb: CSS Reset](http://meyerweb.com/eric/tools/css/reset/)

## Whishlist

- [ ] Item 1

## Sources

| Icon | Category                |
| ---- | ----------------------- |
| 📹   | Video                   |
| 📖   | Documentation / Article |
| ⚙️   | Code                    |
| 🛠    | Tool                    |

| Cat. | Title | Author | Origin |
| ---- | ----- | ------ | ------ |


<!-- | 📹   | Title | Author | [YouTube](https://www.youtube.com/watch?) | -->
