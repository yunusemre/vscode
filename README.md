Başlangıç için kurulması gereken paketler
```
npm install --save-dev eslint prettier eslint-plugin-react eslint-plugin-react-hooks eslint-config-prettier eslint-plugin-prettier husky @typescript-eslint/parser @typescript-eslint/eslint-plugin @trivago/prettier-plugin-sort-imports
```

Eslint için script: 
``` "eslint": "eslint \"src/**/\*.{ts,tsx}\" --quiet --fix" ```

Prettier için script: 
``` "prettier --write" ````

Prettier .prettierrc için: 
```
{
    "arrowParens": "always",
    "bracketSpacing": true,
    "jsxBracketSameLine": false,
    "jsxSingleQuote": true,
    "quoteProps": "as-needed",
    "singleQuote": true,
    "semi": true,
    "printWidth": 100,
    "useTabs": false,
    "tabWidth": 4,
    "trailingComma": "es5",
    "plugins": ["@trivago/prettier-plugin-sort-imports"],
    "importOrderSeparation": true,
    "importOrderSortSpecifiers": true
}
```

Husky için yapılması gerekenler:
```npx husky add .husky/pre-commit "npx lint-staged" ```

```
"husky": {
  "hooks": {
    "pre-commit": "lint-staged"
  }
},
"lint-staged": {
    "src/**/*.{ts,tsx}": [
        "eslint \"src/\*\*/_.{ts,tsx}\" --quiet --fix",
        "prettier --write"
    ]
}
```

```... "prepare": "husky"... ```
