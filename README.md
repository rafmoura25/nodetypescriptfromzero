# Guia pessoal para inicialização de uma app node em typescript

```
// criando o package.json
yarn init -y

// incluindo o typescript
yarn add typescript ts-node-dev @types/node tsconfig-paths -D

// cria o tsconfig
npx tsc --init --rootDir src --outDir build --esModuleInterop --resolveJsonModule --lib es6 --module commonjs --allowJs true --noImplicitAny true

// criando src/server.ts
// incluir em package
"scripts": {
  "dev": "ts-node-dev --inspect --transpile-only --ignore-watch node_modules src/server.ts"
}

// rodando a app
yarn dev

// criando editorconfig
// instalar extensão editorconfig for vscode
// generate editor config no projeto

// configurando o eslint
yarn add -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin

// criação do .eslintrc
{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended"
  ]
}

// .eslintignore
node_modules
dist
build
/*.js

// add no package.json
"scripts": {
  "test": "echo \"Error: no test specified\" &amp;&amp; exit 1",
  "dev": "ts-node-dev --inspect --transpile-only --ignore-watch node_modules src/server.ts",
  "lint": "eslint . --ext .ts"
}

// regras lint
{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended"
  ],
  "rules": { 
    "no-console": "warn"
  }
}

// correção automatica
"scripts": {
  "test": "echo \"Error: no test specified\" &amp;&amp; exit 1",
  "dev": "ts-node-dev --inspect --transpile-only --ignore-watch node_modules src/server.ts",
  "lint": "eslint . --ext .ts",
  "lint-fix": "eslint . --ext .ts --fix"
}

```

prettier
```
yarn add prettier -D

// .prettierrc
{
  "semi": true,
  "trailingComma": "all",
  "singleQuote": true,
  "printWidth": 80,
  "arrowParens": "avoid"
}

yarn add eslint-config-prettier@6.15.0 eslint-plugin-prettier@3.2.0 -D

// Ajustar o arquivo .eslintrc:
{
  "root": true,
  "parser": "@typescript-eslint/parser",
  "plugins": [
    "@typescript-eslint",
    "prettier"
  ],
  "extends": [
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
    "plugin:@typescript-eslint/recommended",
    "prettier/@typescript-eslint",
    "plugin:prettier/recommended"
  ],
  "rules": {
    "no-console": "warn",
    "prettier/prettier": "error"
  }
}
```

```
.
└── src
    ├── config
    ├── modules
    └── shared
        └── http
            └── server.ts
```

```
// ajuste
{
  "scripts": {
    "dev": "ts-node-dev --inspect --transpile-only --ignore-watch node_modules src/shared/http/server.ts"
  }
}

// Iniciamos configurando o objeto paths do tsconfig.json, que permite criar uma base para cada path a ser buscado no projeto, funcionando de forma similar a um atalho:
"paths": {
  "@config/*": ["src/config/*"],
  "@modules/*": ["src/modules/*"],
  "@shared/*": ["src/shared/*"]
}
```

```
yarn add express cors express-async-errors

yarn add -D @types/express @types/cors
```

exemplo .gitignore
```
.idea/
.vscode/
node_modules/
build/
temp/
.env
coverage
ormconfig.json
dist

uploads/*
!uploads/.gitkeep
```
