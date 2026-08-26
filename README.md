# 将棋クイズ

将棋のクイズアプリ。GitHub Pages で公開するための **`index.html` と、その隣に置くアイコン** を置くリポジトリです。

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
cp ../app_template/{apple-touch-icon.png,icon-192.png,icon-512.png,app.webmanifest} .
git add -A && git commit -m "更新の内容"
git push origin main          # main に push すると GitHub Pages が自動で配信し直す
```

## アイコンのファイルも隣に必要

`index.html` は 1 枚もので中身が全部入っていますが、**ホーム画面用のアイコンだけは
別ファイルとして隣に置く必要があります。** iOS は `apple-touch-icon` に
`data:` で埋めこんだ絵を受けつけないためです。

| ファイル | 用途 |
|---|---|
| `apple-touch-icon.png` | ホーム画面に追加したときのアイコン (iOS) |
| `icon-192.png` / `icon-512.png` | manifest 用 (Android・PWA) |
| `app.webmanifest` | アプリ名・アイコンの一覧 |

これらが欠けると、iOS はページの見た目を縮小した絵を勝手にアイコンにしてしまいます。
