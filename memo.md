# how to add Prettier/ESLint/Husky/lint-staged

## Prettier

`npm install --save-dev prettier`

`touch .prettierrc.js`

in .prettierrc.js<br>
`module.exports = {
  singleQuote: true,
  trailingComma: 'all',
  printWidth: 100,
};`

format check<br>
`npx prettier --check ./src`

format fix<br>
`npx prettier --write ./src`

in package.json<br>
`"scripts": {
  ...
  "format": "prettier --check ./src",
  "format:fix": "prettier --write ./src"
},`

## ESLint

`npm install eslint --save-dev`

`npx eslint --init`


`❯ To check syntax and find problems`<br>
`❯ JavaScript modules (import/export)`<br>
`❯ React`<br>
`? Does your project use TypeScript? › Yes`<br>
`✔ Browser`<br>
`❯ JavaScript`


Rules
like in .eslintrc.js<br>
`npm install --save-dev eslint-plugin-functional`

check<br>
`npx eslint ./src`

fix<br>
`npx eslint --fix ./src`

in package.json<br>
`"scripts": {
  ...
  "lint": "eslint ./src",
  "lint:fix": "eslint --fix ./src"
},`

## Husky

`npm install --save-dev husky`
`npm install --save-dev lint-staged`

in package.json<br>
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