# nuxt-typescript
Nuxt.js+TypeScript
## package.jsonを作る
package.jsonに下記を入力
```
{
  "name": "nuxt-typescript",
  "scripts": {
    "dev": "nuxt",
    "build": "nuxt build",
    "generate": "nuxt generate",
    "start": "nuxt start"
  }
}
```

## 依存関係を追加
依存関係として以下を追加する
- nuxt(Nuxt.js本体)
- @nuxt/typescript-build (TypeScriptサポート) [開発依存]
- @nuxt/types (TypeScriptサポート) [開発依存]
- jest (jest) [開発依存]
- @vue/test-utils (jest) [開発依存]
- vue-jest (jest) [開発依存]
- ts-jest (jest) [開発依存]
- @types/jest (jest) [開発依存]
- babel-core@bridge (jest) [開発依存]
- jsdom (jest) [開発依存]
- jsdom-global (jest) [開発依存]
### nuxtを追加
```
$ yarn add nuxt
```
### nuxtを追加(動作確認)
下記の内容で``pages/index.vue``を作成する
```
<template>
  <span>test</span>
</template>
```
### サーバ起動(動作確認)
下記実行後``http://localhost:3000/``開いて「test」と表示されることを確認する
```
yarn dev
```

### Nuxt TypeScriptサポートのパッケージを追加
```
yarn add --dev @nuxt/typescript-build @nuxt/types
```
### Nuxt TypeScriptサポート（設定ファイルなど）
``nuxt.config.js``内の``buildModules``に``@nuxt/typescript-build``を追加する
```
export default {
  buildModules: ['@nuxt/typescript-build']
}
```
``tsconfig.json``を作成する
```
{
  "compilerOptions": {
    "target": "ES2018",
    "module": "ESNext",
    "moduleResolution": "Node",
    "lib": [
      "ESNext",
      "ESNext.AsyncIterable",
      "DOM"
    ],
    "esModuleInterop": true,
    "allowJs": true,
    "sourceMap": true,
    "strict": true,
    "noEmit": true,
    "baseUrl": ".",
    "paths": {
      "~/*": [
        "./*"
      ],
      "@/*": [
        "./*"
      ]
    },
    "types": [
      "@types/node",
      "@nuxt/types"
    ]
  },
  "exclude": [
    "node_modules"
  ]
}

```

### 型宣言ファイルを作成する
``types/vue-shim.d.ts``を作成する
```
declare module "*.vue" {
    import Vue from 'vue'
    export default Vue
}
```

### jestのセットアップ
必要なパッケージをインストールする
```
yarn add --dev jest @vue/test-utils
yarn add --dev vue-jest
yarn add --dev ts-jest @types/jest
yarn add --dev babel-core@bridge
yarn add --dev jsdom jsdom-global
```
package.jsonに下記を追記する
```
"jest": {
  "moduleFileExtensions": [
    "js",
    "ts",
    "vue"
  ],
  "transform": {
    ".*\\.(vue)$": "<rootDir>/node_modules/vue-jest",
    "^.+\\.tsx$": "<rootDir>/node_modules/ts-jest",
    "^.+\\.ts$": "<rootDir>/node_modules/ts-jest",
    "^.+\\.js$": "<rootDir>/node_modules/ts-jest"
  },
  "moduleNameMapper": {
    "^@/(.*)$": "<rootDir>/$1",
    "^~/(.*)$": "<rootDir>/$1"
  },
  "setupFilesAfterEnv": [
    "<rootDir>jest.setup.js"
  ]
}
```
tsconfig.jsonに下記を追記する
```
"types": [
  "jest"
]
```

### eslint
パッケージをインストールする
```
yarn add --dev @nuxtjs/eslint-config-typescript
yarn add --dev eslint
```
``.eslintrc.js``に書く
```
module.exports = {
  extends: [
    '@nuxtjs/eslint-config-typescript'
  ]
}
```

## 参考
https://ja.nuxtjs.org/docs/2.x/get-started/installation  
https://typescript.nuxtjs.org/ja/guide/setup