# CHANGELOG
---
#### **December 27th, 2017**
Add **Flow**: A static type checker by Facebook. It detects inconsistent types in your code. For instance, it will give you an error if you try to use a string where should be using a number.
  - Run `yarn add --dev flow-bin babel-preset-flow babel-eslint eslint-plugin-flowtype`
    - `flow-bin` is the binary to run Flow in our `scripts` tasks.
    - `babel-preset-flow` is the preset for Babel to understand Flow annotations.
    - `babel-eslint` is a package to enable ESLint to *rely on Babel's parser* instead of its own.
    - `eslint-plugin-flowtype` is an ESLint plugin to lint Flow annotations.
  - Update your `.babelrc` file like so:

```javascript
{
  "presets": [
    "env",
    "flow"
  ]
}
```

  - And update `.eslintrc.json` as well:

```javascript
{
  "extends": [
    "airbnb",
    "plugin:flowtype/recommended"
  ],
  "plugins": [
    "flowtype",
    "compat"
  ],
  "rules": {
    "semi": [2, "never"],
    "no-unexpected-multiline": 2,
    "compat/compat": 2
  }
}
```

  - **Note:** The `plugin:flowtype/recommended` contains the instructions for ESLint to us Babel's parser.
  - Chain `flow` to your `test` task:

```JavaScript
"scripts": {
  "start": "babel-node src",
  "test": "eslint src && flow"
},
```

  - Create a `.flowconfig` file at the root of your project containing:

```json
[options]
suppress_comment= \\(.\\|\n\\)*\\flow-disable-next-line
```
