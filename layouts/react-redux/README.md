# LAYOUT - REACT REDUX

A layout for a `react`, `redux` client with basic `express` server.

## TODO
- [ ] Add production build steps
    - [ ] UglifyJS2
- [ ] Tests
    - [ ] Unit tests with `mocha`
    - [ ] Integration tests with `karma`
- [ ] Consider hotreloading if necessary

## Features
- [x] Build
    - [x] Webpack
    - [x] File watching
    - [x] Livereload
    - [x] Preconfigured gulp tasks & sane defaults
    - [x] Stylus & CSS packaging and url resolution
    - [x] File resolving & packaging
    - [x] React/Redux structure
    - [x] Mocha test infrastructure
    - [x] ES Linting checks
    - [x] `process.env.NODE_ENV` on client
    - [ ] Minified builds

- [x] Consistant, optimized babel featureset on client & server
- [x] EJS templating
- [x] Isomorphic structure
- [x] Minimal express server
- [x] Isomorphic mocha testing
- [ ] Karma integration tests

## Installation
- Clone this repo
- `cd layouts/react-redux`
- `npm run install_all`
- `npm run start` to build the client, watch the server for changes & `npm start` it

## Configs
Configs should exist throughout the app as necessary and follow a basic structure:
- `default.js` the defaults which are built on top of
- `production.js` a complete production config
- `development.js` a complete development config
- `index.js` is the current env
- `lutils` package for cloning & merging recursively.

The rest of the config structure is up to the data.
Ensure that any development/machine/local specific configs are in a `.gitignore`, with an accompanying `*.template.js` to ensure reproducability.

When configs need to be shared in both client and server, create a root config which only includes that data, as a client sharing a server config could be a security issue.

## NPM
`package.json` should exist in these places:
- `./package.json` build, deployment etc.
- `./server/package.json` server only packages
- `./client/package.json` client only packages

`scripts` in the root `package.json` should exist to install, test, build, start etc.

## Optionals
- `./deploy` as necessary
- `./docs` as necessary
- `./client/`
    - `./stores -> store.js` if the app will only have one store
    - `./sources` as necessary

## Tests
Tests should be inlined within each app. Consider this structure:

```html
./client
    ./__test
        index.spec.js

    ./actions
        ./__test
            doSomething.spec.js
            somethingElse.spec.js

        doSomething.js
        somethingElse.js

    index.js
```

Tests are then run using a glob `/**/*.spec.js` with mocha.

## Variants
- `MULTI APP`
    - Rename `client` with `clients`, add client nesting
    - Rename `server` with `servers`, add server nesting
