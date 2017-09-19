# Gravity Payment's tslint config

This is the tslint configuration that we use at Gravity Payments. Follow the steps below to add this to any TypeScript project.

## Using in a TS project

make sure you have the peer dependencies
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

run the linter

(need to have tslint, and typescript installed globally)
```bash
$ npm install -g tslint typescript
```

then, run this command
```bash
$ tslint --project ./tsconfig.json
```

## strictNullChecks

The `strict-type-predicates` tslint rule requires that your tsconfig.json file has the `strictNullChecks` prop set to true. To do this, make sure your tsconfig.json file has the following prop. (Here)[https://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-0.html] is some more info on this.
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

## Setting up vscode to run tslint

You can configure vscode to run tslint automatically.

but idk how right now, so we need to update this portion of the documentation.
