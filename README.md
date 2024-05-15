# Prettier Eslint Config

This repo contains my current configuration of `prettier.config.js` and `.eslintrc.cjs` files.
I use this configuration in my **next.js production** apps.

## Why use strict EsLint config?

Using strict eslint eliminates the possibilities of bad code ending up in production.
This configuration in particular is designed to save you time by not needing to run a build script as often as you would without it.

## Why use this Prettier config?

This prettier config is designed to make code across your codebase consistent.
It uses pleasing syntax, removing unnecessary things such as semi-columns.

## How to use?

You can use by copying the files from repo to your own, or by copy & pasting the code below.

## Prerequisites

You will need to have EsLint, Prettier and Prettier Tailwind Plugin installed as dev dependencies in your project.

### Adding EsLint to your project

You can refer to the official [EsLint docs](https://eslint.org/docs/latest/use/getting-started).

### Adding Prettier to your project

You can refer to the official [Prettier docs](https://prettier.io/docs/en/install.html).

### Install Prettier TailwindCSS plugin

Only use this if you are using TailwindCSS in your project.

```shell
pnpm add -D prettier-plugin-tailwindcss
```

## Code Snippets

`.eslintrc.cjs`

```cjs
/** @type {import("eslint").Linter.Config} */
const config = {
  parser: "@typescript-eslint/parser",
  parserOptions: {
    project: true,
  },
  plugins: ["@typescript-eslint"],
  extends: [
    "next/core-web-vitals",
    "plugin:@typescript-eslint/recommended-type-checked",
    "plugin:@typescript-eslint/stylistic-type-checked",
  ],
  rules: {
    "@typescript-eslint/array-type": "off",
    "@typescript-eslint/consistent-type-definitions": "off",
    "@typescript-eslint/consistent-type-imports": [
      "warn",
      {
        prefer: "type-imports",
        fixStyle: "inline-type-imports",
      },
    ],
    "@typescript-eslint/no-unused-vars": [
      "warn",
      {
        argsIgnorePattern: "^_",
      },
    ],
    "@typescript-eslint/require-await": "off",
    "@typescript-eslint/no-misused-promises": [
      "error",
      {
        checksVoidReturn: {
          attributes: false,
        },
      },
    ],
  },
}
module.exports = config
```

`prettier.config.js`

```js
/** @type {import('prettier').Config & import('prettier-plugin-tailwindcss').PluginOptions} */
const config = {
  semi: false,
  singleQuote: false,
  trailingComma: "all",
  plugins: ["prettier-plugin-tailwindcss"],
}

export default config
```

## License

You are free to use, modify and distribute all code in this repo without any need for contributions or purchases.
