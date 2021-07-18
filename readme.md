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


## 参考
https://ja.nuxtjs.org/docs/2.x/get-started/installation
