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

TODO: fill this out


## Setting up vscode to run tslint

You can configure vscode to run tslint while you are editing code.

TODO: fill this out
