# 将棋 タイトル年表 / 級の記録

GitHub Pages で公開している、2 枚のページです。

**https://kakugawari.github.io/shogi_quiz/**

| ファイル | 中身 |
|---|---|
| `index.html` | 将棋の歴代タイトルホルダーの年表 (8 タイトルを横にならべた表と、棋戦ごとの年表) |
| `kyu.html` | 子どもの級位・段位があがってきた記録 (いまの級、グラフ、年表) |
| `site.css` | 2 枚で共通の見た目 |

もとは将棋クイズでしたが、クイズはやめて年表だけにしました。
クイズのころのソースは [`kakugawari/app_template`](https://github.com/kakugawari/app_template) に残っています。
いまは **このリポジトリのファイルを直接直します** (ビルドはありません)。

## タイトル年表を足す

`index.html` の `KISEN` に、棋戦ごとに `'2026 藤井聡太'` の形で 1 行足します。
いまの保持者と通算期数は `GENZAI` に書きます。

## 級の記録を足す

`kyu.html` の `KIROKU.rows` に 1 行足します。

```js
{ date: '2026-08-15', rank: '初段', where: '〇〇将棋教室', memo: 'ひとこと' },
```

- `date` は `YYYY-MM-DD` (日がわからなければ `YYYY-MM`)
- `rank` は `15級` / `1級` / `初段` / `二段` など
- `where` がちがう記録 (道場とネット将棋など) は、グラフで別の線になります

## アイコンのファイルも隣に必要

iOS は `apple-touch-icon` に `data:` で埋めこんだ絵を受けつけないため、
ホーム画面用のアイコンは別ファイルとして置いています。

| ファイル | 用途 |
|---|---|
| `apple-touch-icon.png` | ホーム画面に追加したときのアイコン (iOS) |
| `icon-192.png` / `icon-512.png` | manifest 用 (Android・PWA) |
| `app.webmanifest` | アプリ名・アイコンの一覧 |
