# How To Set Up ESLint, TypeScript, Prettier with Create React App

First, let's install or devDependencies
```
npm i -D @types/react @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-prettier eslint-config-react eslint-plugin-prettier prettier
```

Your devDependecies in **package.json** should now look like this,
```
"devDependencies": {
  "@typescript-eslint/eslint-plugin": "^1.6.0",
  "@typescript-eslint/parser": "^1.6.0",
  "eslint-config-prettier": "^4.1.0",
  "eslint-config-react": "^1.1.7",
  "eslint-plugin-prettier": "^3.0.1",
  "prettier": "^1.16.4"
}
```

Now create two files in your projects root (same level as your src folder).
```
.eslintignore
.eslintrc.json
```

In your **.eslintrc.json** add
```
{
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier/@typescript-eslint",
    "plugin:prettier/recommended"
  ],
  "plugins": ["react", "@typescript-eslint", "prettier"],
  "env": {
    "browser": true,
    "jasmine": true,
    "jest": true
  },
  "rules": {
    "prettier/prettier": ["error", { "singleQuote": true }]
  },
  "settings": {
    "react": {
      "pragma": "React",
      "version": "detect"
    }
  },
  "parser": "@typescript-eslint/parser"
}
```

and in your .eslintignore add any paths you don't want linted. In my case, I want to exclude my tests folders and the service worker that is packaged with CRA
```
src/registerServiceWorker.js
src/**/__tests__/**
```

In your package.json file we're going to add a new scripts file that will allow us to run our linter. Next to your react `start`, `build`, and `test` scripts add
