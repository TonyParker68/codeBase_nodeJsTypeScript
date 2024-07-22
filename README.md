# Setting Up a TypeScript Node.js Project

### Step 1: Initialize the Project

Initialize a new Node.js project with a package.json file. The `-y` flag skips the prompts and uses default settings, which you can modify later.

```bash
npm init -y
```

### Step 2: Install TypeScript as a Dev Dependency

Install TypeScript to start using it in your project.

```bash
npm install typescript --save-dev
```

### Step 3: Install TypeScript Types for Node.js

Install the type definitions for Node.js.

```bash
npm i @types/node -D
```

### Step 4: Install Required Config Packages

Install essential packages for configuration and development.

```bash
npm i eslint prettier eslint-config-prettier eslint-plugin-prettier @typescript-eslint/eslint-plugin @typescript-eslint/parser ts-node tsc-alias tsconfig-paths rimraf nodemon -D
```

```
Explanation of Installed Packages:
- eslint: Main linter for checking code quality.
- prettier: Code formatter.
- eslint-config-prettier: Configures ESLint to avoid conflicts with Prettier.
- eslint-plugin-prettier: Integrates Prettier rules into ESLint.
- @typescript-eslint/eslint-plugin: ESLint plugin for TypeScript.
- @typescript-eslint/parser: Parser for ESLint to understand TypeScript.
- ts-node: Allows running TypeScript files directly.
- tsc-alias: Handles alias paths during build.
- tsconfig-paths: Resolves paths in tsconfig.json for ts-node.
- rimraf: Removes directories (used for cleaning up before builds).
- nodemon: Automatically restarts the server on code changes.
```

### Step 5: Configure TypeScript

Create a tsconfig.json file in the root directory with the following configuration:

```json
{
  "compilerOptions": {
    "module": "NodeNext",
    "moduleResolution": "NodeNext",
    "target": "ES2022",
    "outDir": "dist",
    "esModuleInterop": true,
    "strict": true,
    "skipLibCheck": true,
    "baseUrl": ".",
    "paths": {
      "~/*": ["src/*"]
    }
  },
  "ts-node": {
    "require": ["tsconfig-paths/register"]
  },
  "files": ["src/type.d.ts"],
  "include": ["src/**/*"]
}
```

### Step 6: Configure ESLint

Download Eslint and Prettier extensions in VS Code.
Create a .eslintrc file in the root directory:

```json
{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": ["@typescript-eslint", "prettier"],
  "extends": ["eslint:recommended", "plugin:@typescript-eslint/recommended", "eslint-config-prettier", "prettier"],
  "rules": {
    "@typescript-eslint/no-explicit-any": "off",
    "@typescript-eslint/no-unused-vars": "off",
    "prettier/prettier": [
      "warn",
      {
        "arrowParens": "always",
        "semi": true,
        "trailingComma": "all",
        "tabWidth": 2,
        "endOfLine": "auto",
        "useTabs": false,
        "singleQuote": false,
        "printWidth": 120,
        "jsxSingleQuote": false,
        "singleAttributePerLine": true
      }
    ]
  }
}
```

Also, create an .eslintignore file to ignore certain files and directories:

```json
node_modules/
dist/
```

### Step 7: Configure Prettier

Create a .prettierrc file in the root directory:

```json
{
  "arrowParens": "always",
  "semi": true,
  "trailingComma": "all",
  "tabWidth": 2,
  "endOfLine": "auto",
  "useTabs": false,
  "singleQuote": false,
  "printWidth": 120,
  "jsxSingleQuote": false,
  "singleAttributePerLine": true
}
```

Create a .prettierignore file to ignore certain files and directories:

```json
node_modules/
dist/
```

### Step 8: Configure Editor

Create a .editorconfig file to ensure consistent editor settings:

```json
indent_size = 2
indent_style = space
```

### Step 9: Configure Git Ignore

Create a .gitignore file to ignore certain files and directories from being committed:

```json
node_modules/
dist/
```

### Step 10: Configure Nodemon

Create a nodemon.json file to configure nodemon:

```json
{
  "watch": ["src"],
  "ext": ".ts,.js",
  "ignore": [],
  "exec": "npx ts-node ./src/index.ts"
}
```

### Step 11: Configure Scripts in package.json

Update the scripts section in your package.json file:

```json
"scripts": {
  "dev": "npx nodemon",
  "build": "rimraf ./dist && tsc && tsc-alias",
  "start": "node dist/index.js",
  "lint": "eslint .",
  "lint:fix": "eslint . --fix",
  "prettier": "prettier --check .",
  "prettier:fix": "prettier --write ."
}
```

### Step 12: Create Global Type Definition File

Create a src/type.d.ts file. This file can be empty for now. Its purpose is to define global types for your project.

```typescript
// You can define global types here
```

By following these steps, you should have a fully configured TypeScript Node.js project ready for development. Happy coding!
