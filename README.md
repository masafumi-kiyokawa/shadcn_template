# React + TypeScript + Vite

このテンプレートは、ViteでReactを動作させるための最小限のセットアップを提供し、HMRといくつかのESLintルールを含んでいます。

現在、2つの公式プラグインが利用可能です:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) は [Babel](https://babeljs.io/) を使用してFast Refreshを実現します
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) は [SWC](https://swc.rs/) を使用してFast Refreshを実現します

## ESLint設定の拡張

本番アプリケーションを開発する場合、型認識のリントルールを有効にするために設定を更新することをお勧めします:

- トップレベルの `parserOptions` プロパティを次のように設定します:

```js
export default tseslint.config({
  languageOptions: {
    // 他のオプション...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

- `tseslint.configs.recommended` を `tseslint.configs.recommendedTypeChecked` または `tseslint.configs.strictTypeChecked` に置き換えます
- 必要に応じて `...tseslint.configs.stylisticTypeChecked` を追加します
- [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) をインストールし、設定を更新します:

```js
// eslint.config.js
import react from 'eslint-plugin-react'

export default tseslint.config({
  // Reactのバージョンを設定
  settings: { react: { version: '18.3' } },
  plugins: {
    // Reactプラグインを追加
    react,
  },
  rules: {
    // 他のルール...
    // 推奨ルールを有効にする
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
```

---

# 以下加筆部分
## npm
Windowsは以下からインストール<br>
https://nodejs.org/en

MacOS
```
brew install node
```

インストール確認
```
npm -v
```


## リポジトリのクローン
```
git clone https://github.com/masafumi-kiyokawa/shadcn_template.git
cd colabo_frontend
npm install
npm run dev
```

## Docker

以下からインストール<br>
https://www.docker.com/

インストール確認
```
docker -v
```

## Dockerコマンド
プロジェクトルートで実行

```
#主に初回のコンテナ起動時、すでにあるイメージを使用してコンテナを起動する時に使用
$ docker compose up -d

#Dockerfileやcompose.yamlを編集した時に使用
#依存関係に更新があった場合も使用(先にコンテナを終了しておくこと)
$ docker compose up -d --build

#コンテナに入る時に使用 appはcompose.yamlのservicesの名前
$ docker compose exec app bash

#コンテナを修了する時に使用
$ docker compose down
```

## 参考URL
https://qiita.com/shoki-y/items/1be906c372c8a9a993a3
https://v0.dev/chat/kEHGSZl6edt
https://ui.shadcn.com/docs/installation/vite
https://tailwindcss.com/docs/guides/vite
https://ja.react.dev/
https://reactrouter.com/en/main/start/faq