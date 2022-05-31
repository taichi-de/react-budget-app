# how to add Prettier/ESLint/Husky/lint-staged

## Prettier

`npm install --save-dev prettier`

`touch .prettierrc.js`

in .prettierrc.js
`module.exports = {
  singleQuote: true,
  trailingComma: 'all',
  printWidth: 100,
};`

format check
`npx prettier --check ./src`

format fix
`npx prettier --write ./src`

in package.json
`"scripts": {
  ...
  "format": "prettier --check ./src",
  "format:fix": "prettier --write ./src"
},`

## ESLint

`npm install eslint --save-dev`

`npx eslint --init`

❯ To check syntax and find problems
❯ JavaScript modules (import/export)
❯ React
? Does your project use TypeScript? › Yes
✔ Browser
❯ JavaScript

Rules
like in .eslintrc.js
`npm install --save-dev eslint-plugin-functional`

check
`npx eslint ./src`

fix
`npx eslint --fix ./src`

in package.json
`"scripts": {
  ...
  "lint": "eslint ./src",
  "lint:fix": "eslint --fix ./src"
},`

## Husky

`npm install --save-dev husky`
`npm install --save-dev lint-staged`

in package.json
`{
  ...
  "scripts": {
    ...
  },
  "lint-staged": {
    "src/**/*.{ts,tsx}": [
      "eslint --ext .tsx --ext .ts ./src --fix"
    ],
    "./src/**": [
      "prettier --write ."
    ]
  },
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  ...
}`



