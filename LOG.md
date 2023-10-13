### setting
typescript用のESlintをインストール
```bash
npm install --save-dev @typescript-eslint/eslint-plugin
```
.eslintrc.jsonに追加
```json
{
  "extends": [ 
    "plugin:@typescript-eslint/recommended", //追加
    "next/core-web-vitals"
]
}
```
エラー出ないか確認(以下のようになればOK)
```bash
npm run lint
✔ No ESLint warnings or errors
```

pritterをインストール
```bash
npm install --save-dev prettier
```
.prettier.jsonを作成
```json
{
  "tabWidth": 2,
  "printWidth": 100,
  "trailingComma": "es5",
  "semi": true,        // falseを設定することが多いが、バグりやすいので、trueを設定
  "singleQuote": true
}
```

Prettierが整形した箇所に対して、eslintでエラーが出ないようにする。
```bash
npm install --save-dev eslint-config-prettier
```

.eslintrc.jsonに追加
```json
{
  "extends": [
    "plugin:@typescript-eslint/recommended",
    "next/core-web-vitals",
    "prettier" //追加
  ]
}
```

package.jsonに追加
```json
"format": "prettier --write --ignore-path .gitignore './**/*.{js,jsx,ts,tsx,json,css,scss}' && next lint --fix"
```
エラー出ないか確認(以下のようになればOK)
```bash
✔ No ESLint warnings or errors
```

VSCodeの設定
.vscode/settings.jsonを作成
ファイルの保存時に、自動でフォーマッタが動作するように設定する
```json
{
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll": true,
      "source.organizeImports": true
    },
    "prettier.configPath": ".prettierrc.json",
    "typescript.tsdk": "node_modules/typescript/lib"
}
```