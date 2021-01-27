# Rollup.js introduction

This example project demonstrates how to use [Rollup.js](https://rollupjs.org/) to bundle JavaScript files. It accompanies [this article](https://www.sitepoint.com/rollup-javascript-bundler-introduction/) on SitePoint.

## Requirements

* [Node.js](http://nodejs.org/) 

## Installation Steps

Clone the project then run `npm install` to install all dependencies.

The project provides JavaScript which shows a realtime digital clock on an HTML page. A server can be started with `npm run server` so you can access pages at <http://localhost:8888/>, e.g. <http://localhost:8888/index.original.html>

Rollup.js is installed locally and all configuration files are provided in the `config` directory.


## Quick start example

Run:

```bash
npm run quickstart
```

or

```bash
npx rollup ./src/main.js --file ./build/bundle.js --format iife --sourcemap inline
```

A single `build/bundle.js` file is created from the source files with an inline sourcemap.

Start the server with `npm run server` then load <http://localhost:8888/index.html>


## Automatic bundling

Run:

```bash
npm run quickstart:watch
```

or

```bash
npx rollup ./src/main.js --file ./build/bundle.js --format iife --sourcemap inline --watch --no-watch.clearScreen
```

JavaScript files in the `src` directory are automatically bundled when changes occur.


## Simple configuration file

Run:

```bash
npm run simple
```

or

```bash
npx rollup --config ./config/rollup.simple.js
```

to use the `./config/rollup.simple.js` configuration file which is identical to the quick start example.

Run `npm run simple:watch` for automatic bundling. Note that `watch` options can be defined in the configuration file, but `--watch` must still be added as a `rollup` command-line flag.


## Development and production modes

Environment variables can be passed to the configuration file using the `rollup --environment` flag, e.g.

```bash
npx rollup --config ./config/rollup.devprod.js --environment NODE_ENV:development
npx rollup --config ./config/rollup.devprod.js --environment NODE_ENV:production
```

This configuration removes the sourcemap in `production` mode.


## Use npm modules

Node.js npm modules can be included in bundled scripts with the [`node-resolve`](https://github.com/rollup/plugins/tree/master/packages/node-resolve) and [`plugin-commonjs`](https://github.com/rollup/plugins/tree/master/packages/commonjs) plugins.

The [day.js date library](https://day.js.org/) has been installed (using `npm install dayjs --save-dev`).

It has been used in `src/main-dayjs.js` which can be bundled with:

```bash
npm run nodemodule
```

or

```bash
npx rollup --config ./config/rollup.npm.js
```


## Replace tokens

The Rollup.js [replace plugin](https://github.com/rollup/plugins/tree/master/packages/replace) can replace strings. The `config/rollup.replace.js` configuration file defines a `tokens` object which replaces references in `src/main-replace.js`. Bundle with:

```bash
npm run replace
```

or

```bash
npx rollup --config ./config/rollup.replace.js
```


## Bundle ES5 and ES6

The [Buble plugin](https://github.com/rollup/plugins/tree/master/packages/buble) can transpile ES6 to ES5. Bundle both ES6 `build/bundle.mjs` and ES5 `build/bundle.js` scripts using:

```bash
npm run es5
```

or

```bash
npx rollup --config ./config/rollup.es5.js
```

Start the server with `npm run server` then load <http://localhost:8888/index.es5.html>. The clock now works in IE11 as well as modern browsers.


## Minify output

Bundle and minify both ES6 `build/bundle.mjs` and ES5 `build/bundle.js` scripts using the [Terser plugin](https://github.com/TrySound/rollup-plugin-terser):

```bash
npm run minify
```

or

```bash
npx rollup --config ./config/rollup.minify.js
```


## Output production code

Create final minified production code:

```bash
npm run build
```

or

```bash
npx rollup --config ./config/rollup.minify.js --environment NODE_ENV:production
```

## License

SitePoint's code archives and code examples are licensed under the MIT license.

Copyright © 2021 SitePoint

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
