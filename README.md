# Gravity Payment's tslint config

This is the tslint configuration that we use at Gravity Payments. Follow the steps below to add this to any TypeScript project.

## Using in a TS project

make sure you have all the peer dependencies installed
```bash
$ yarn add --dev typescript tslint
```

install this project as a dependency
```bash
$ yarn add --dev tslint-config-gravity
```

add a `tslint.json` file in the root dir that looks like this
```json
{
    "extends": "tslint-config-gravity"
}
```
this tells tslint to grab the `tslint.json` file at `./node_modules/tslint-config-gravity`

 make sure you have tslint and typescript installed globally

```bash
$ npm install -g tslint typescript
```

now run the linter

```bash
$ tslint --project ./tsconfig.json
```

## strictNullChecks

The `strict-type-predicates` tslint rule requires that your tsconfig.json file has the `strictNullChecks` prop set to true. To do this, make sure your tsconfig.json file has the following prop. [Here](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-0.html) is some more info on this.
```json
{
    "compilerOptions": {
        "strictNullChecks": true
    }
}
```

## Auto fixing

tslint has the option to auto fix some of the simpler checks. To do this, simply add the `--fix` flag when you run the tslint command.
```bash
$ tslint --project tsconfig.json --fix
```

## Using with webpack

You can setup webpack to run your code through tslint during the bundle process. Errors will not prevent your code from being bundled, but will provide warnings in the console. To set this up follow the instructions below.

install the `tslint-webpack-plugin`
```bash
$ yarn add --dev tslint-webpack-plugin
```

edit your webpack config file to include the following
```javascript
const TSLintPlugin = require('tslint-webpack-plugin');

module.exports = {
    plugins: [
        new TSLintPlugin({
            files: ['./path/to/ts/files/**/*.ts', './another/path/**.tsx'],
            project: './tsconfig.json'
        })
    ]
}
```

then run webpack. you will see warnings in terminal after the webpack output like...
```bash
Hash: eb3f77073bfc7eb5a3d3
Version: webpack 3.5.5
Child index:
    Hash: eb3f77073bfc7eb5a3d3
    Time: 3503ms
        Asset     Size  Chunks                    Chunk Names
    bundle.js  1.17 MB       0  [emitted]  [big]  main
       [7] ./node_modules/react/react.js 56 bytes {0} [built]
      [10] ./node_modules/mobx/lib/mobx.module.js 142 kB {0} [built]
      [12] ./node_modules/mobx-react/index.js 29.7 kB {0} [built]
      [20] ./node_modules/react/lib/React.js 5.08 kB {0} [built]
      [29] ./src/actions/index.ts 2.08 kB {0} [built]
      [30] ./node_modules/@trevorhanus/reactx/dist/index.js 650 bytes {0} [built]
      [39] ./node_modules/@trevorhanus/reactx/dist/router/Router.js 8.63 kB {0} [built]
      [42] ./node_modules/react-dom/index.js 59 bytes {0} [built]
     [102] multi ./src/index.tsx 28 bytes {0} [built]
     [103] ./src/index.tsx 695 bytes {0} [built]
     [215] ./src/routes/routes.ts 1.65 kB {0} [built]
     [233] ./src/components/App.tsx 698 bytes {0} [built]
     [238] ./src/components/Auth.tsx 642 bytes {0} [built]
     [242] ./src/stores/Store.ts 1.27 kB {0} [built]
     [243] ./src/stores/TodoStore.ts 4.53 kB {0} [built]
        + 230 hidden modules

[tslint-plugin] Starting linter in separate process...

/Users/thanus/dev/reactx-todo/src/actions/index.ts
[Error 35,9]: Expression is always true. (strict-type-predicates)

/Users/thanus/dev/reactx-todo/src/routes/routes.ts
[Error 36,21]: Expression is always true. (strict-type-predicates)
[Error 36,46]: Expression is always true. (strict-type-predicates)

/Users/thanus/dev/reactx-todo/src/components/AddTodoControl.tsx
[Error 19,13]: Expression is always true. (strict-type-predicates)

/Users/thanus/dev/reactx-todo/src/components/TodoFooter.tsx
[Error 17,24]: Expression is always true. (strict-type-predicates)
[Error 29,55]: Use '=== undefined' instead. (strict-type-predicates)

[tslint-plugin] Linting complete.
```

## Setting up vscode to run tslint

You can configure vscode to run tslint while you are editing code.

open the extensions window `shift+command+x`

search for 'tslint' and install the *TSLint for Visual Studio Code* extension

restart VSCode and it should be linting!
