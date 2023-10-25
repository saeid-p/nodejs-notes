# Node JS
My notes for setting up and managing a node project.

- Run `npm init -y` to setup basic files. [Read more](https://docs.npmjs.com/cli/v8/commands/npm-init)
- Intall TypeScript: `npm install --save-dev typescript`
- Create a `tsconfig.json` in the root folder with the following configurations:
```
{
  "compilerOptions": {
    "module": "commonjs", // Specifies the module code generation method. Node uses `commonjs`
    "target": "es6", // Specifies the output language level.
    "moduleResolution": "node",
    "sourceMap": true,
    "outDir": "dist",
    "esModuleInterop": true
  },
  "lib": ["es2015"]
}
```
- To manually compile typescript, run `tsx tsc`
- Install eslint with `npm install --save-dev eslint`
- Run `npm init @eslint/config`. This will ask you a series of questions.
- Update the `eslintrc.js` file with the following content:
```
module.exports = {
  env: {
    es2021: true,
    node: true,
  },
  extends: ["eslint:recommended", "plugin:@typescript-eslint/recommended"],
  parser: "@typescript-eslint/parser",
  parserOptions: {
    ecmaVersion: 13,
    sourceType: "module",
  },
  plugins: ["@typescript-eslint"],
  rules: {},
};
```
- Run `npx eslint . --ext .ts` for testing the config.
- Update the `package.json` file with the following content:
```
"main": "dist/app.js",
"scripts": {
  "start": "tsc && node dist/app.js",
  "lint": "eslint . --ext .ts",  
}
```
- Now run `npm start` to see the output of your file.
