# Tailwind CLI (command line interface) 


## 0. 準備

> [!TIP]
解説動画：https://youtu.be/0ZImKleAuUY

1. プロジェクトフォルダ（作業するフォルダ）を作成
2. Node.js はインストール必須
3. index.html を作成
4. css/output.css を作成


## 1．tailwindcssとautoprefixerをインストール
```
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init
```


## 2．下記のフォルダやファイルが自動生成されます。
```
node_modules/*
package-lock.json
package.json
tailwind.config.js
```

## 3．css/input.cssを作成➡以下3行を追加記述
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```

## 4．tailwind.config.jsの”content”内を修正
```
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "*.{html,php}",
    './js/*.{js,ts,jsx,tsx}'
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
```

## 5．以下コマンドを打つ！→ post.config.js作成（設定用ファイル）
```
npx tailwindcss init -p
```

## 6．package.jsonの記述を修正
> [!IMPORTANT]
以下"scripts"だけ変える
```
{
  "devDependencies": {
    "autoprefixer": "^10.4.13",
    "postcss": "^8.4.21",
    "tailwindcss": "^3.2.4"
  },
  "scripts": {
    "dev": "tailwindcss -i ./css/input.css -o ./css/output.css --watch"
  }
}
```

## 7．以下コマンドを打つ！→ dist.cssに自動でスタイルが追加される
```
npm run dev
```

## 8．HTML側にCSSファイル読み込みを追記
```
<link rel="stylesheet" href="./css/output.css">
```

## 補足
> [!TIP]
JavaScript側からclassを追加する処理がある場合
1. jsフォルダ作成
2. main.js作成 以下を記述
3. document.querySelector("h1").classList.add("text-blue-300");
4. HTMLにh1要素を追加
5. npm run dev
6. output.cssのCSSを確認 (追加されてますか？)




以上

