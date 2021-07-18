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



## 参考
https://ja.nuxtjs.org/docs/2.x/get-started/installation
