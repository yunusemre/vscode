Başlangıç için kurulması gereken paketler
```
npm install --save-dev eslint prettier eslint-plugin-react eslint-plugin-react-hooks eslint-config-prettier eslint-plugin-prettier husky @typescript-eslint/parser @typescript-eslint/eslint-plugin @trivago/prettier-plugin-sort-imports
```

Eslint için script: 
``` "eslint": "eslint \"src/**/\*.{ts,tsx}\" --quiet --fix" ```
Eslint için .eslintrc

```
{
    "root": true,
    "env": { "browser": true, "es2020": true },
    "extends": [
        "eslint:recommended",
        "plugin:@typescript-eslint/recommended",
        "plugin:react-hooks/recommended",
        "plugin:react/recommended",
        "plugin:prettier/recommended",
    ],
    "ignorePatterns": ["dist", ".eslintrc"],
    "parser": "@typescript-eslint/parser",
    "plugins": ["react-refresh", "react", "react-hooks", "@typescript-eslint"],
    "rules": {
        "react-refresh/only-export-components": ["warn", { "allowConstantExport": true }],
        "react/react-in-jsx-scope": 0,
    },
    "settings": {
        "react": {
            "version": "detect",
        },
    },
}
```

Prettier için script: 
``` "prettier --write" ```

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

package.json içerisine eklenecekler: 
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

```"prepare": "husky" ```

Dosya yolu için yapılması gerekenler:

```
"baseUrl": ".",
"paths": {
    "@/*": ["./src/*"]
},
"include": ["src/**/*.ts", "src/**/*.d.ts", "src/**/*.tsx"],
"exclude": ["node_modules", "dist"],
```

vite config için yapılması gerekenler:

```

import tsconfigPaths from 'vite-tsconfig-paths'; // must installl

export default defineConfig({
    plugins: [react(), tsconfigPaths()],
    resolve: {
        alias: {
            '@': path.resolve(__dirname, './src'),
        },
    },
});
```


