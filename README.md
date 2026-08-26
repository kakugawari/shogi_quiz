# しょうぎクイズ道場

将棋のクイズアプリ。GitHub Pages で公開するための **1枚ものの `index.html`** だけを置くリポジトリです。

**https://kakugawari.github.io/shogi_quiz/**

## ソースはここではない

このアプリの元のソース（HTML/CSS/JS を分けたもの、テスト、クイズの中身）は
[`kakugawari/app_template`](https://github.com/kakugawari/app_template) にあります。
`index.html` は、あちらで `npm run build` を実行して作った 1 枚ものの出力を
そのまま置いたものです。

**このリポジトリの `index.html` を直接編集しないでください。** 直すのは `app_template` 側のソースで、
直したら `npm run build` → 出てきた `shogi-quiz-dojo.html` をこのリポジトリの `index.html` として
置き換えてください。

## 更新のしかた

```bash
# app_template 側で
npm test && npm run test:ui   # 直したら必ず両方確かめる
npm run build                 # shogi-quiz-dojo.html ができる

# shogi_quiz 側で
cp ../app_template/shogi-quiz-dojo.html index.html
git add index.html && git commit -m "更新の内容"
git push origin main          # main に push すると GitHub Pages が自動で配信し直す
```
