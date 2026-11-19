# ひな将棋 (ひなの歴史 / 勝率チェック / タイトル年表)

GitHub Pages で公開している、タイトル画面と 3 枚のページです。

**https://kakugawari.github.io/shogi_quiz/**

| ファイル | 中身 |
|---|---|
| `index.html` | **タイトル画面** (アプリを開くと最初に出る)。「ひな将棋」のロゴと教室の料金表。画面のどこを押しても「ひなの歴史」へ。料金は中の `RYOUKIN` で直す |
| `hina.html` | **ひなの歴史**。級位があがってきた記録 (いまの級、グラフ、学年ごとの道のり) |
| `title-bg.jpg` / `title-logo.png` | タイトル画面の背景 (アイコンと同じ紺の盤) と、筆文字のロゴ |
| `shoritsu.html` | リーグ戦の勝率チェック。勝ち・負けの数をドラムで回して選ぶ (数はその端末にだけ残る) |
| `titles.html` | おまけ: 将棋の歴代タイトルホルダーの年表 (8 タイトルを横にならべた表と、棋戦ごとの年表) |
| `kyu.html` | 前の「ひなの歴史」のアドレス。開くと `hina.html` へ飛ぶ (古いブックマーク用) |
| `site.css` | 3 枚で共通の見た目 |

もとは将棋クイズでしたが、クイズはやめて、いまは「ひなの歴史」が中心のアプリです。
クイズのころのソースは [`kakugawari/app_template`](https://github.com/kakugawari/app_template) に残っています。
いまは **このリポジトリのファイルを直接直します** (ビルドはありません)。

## ひなの歴史に記録を足す

`hina.html` の `KIROKU.rows` に 1 行足します。

```js
{ date: '2026-08-15', rank: '初段', where: '〇〇将棋教室', memo: 'ひとこと' },
```

- `date` は `YYYY-MM-DD` (日がわからなければ `YYYY-MM`)
- `rank` は `15級` / `1級` / `初段` / `二段` など
- 学年は `KIROKU.gakunen` (何年度に何年生か) から数えます。4月になると次の学年の箱が自動でできます
- 大会・タイトル戦は `KIROKU.dekigoto` に `{ date, name, koma, kekka }` で足すと、グラフに金の駒の印と、下の「大会・タイトル戦」に出ます
- `where` がちがう記録 (道場とネット将棋など) は、グラフで別の線になります

## タイトル年表を足す

`titles.html` の `KISEN` に、棋戦ごとに `'2026 藤井聡太'` の形で 1 行足します。
いまの保持者と通算期数は `GENZAI` に書きます。

## アイコンのファイルも隣に必要

iOS は `apple-touch-icon` に `data:` で埋めこんだ絵を受けつけないため、
ホーム画面用のアイコンは別ファイルとして置いています。

| ファイル | 用途 |
|---|---|
| `apple-touch-icon.png` | ホーム画面に追加したときのアイコン (iOS) |
| `icon-192.png` / `icon-512.png` | manifest 用 (Android・PWA) |
| `app.webmanifest` | アプリ名・アイコンの一覧 |

## iPhone のホーム画面から開くとき

app_template と同じやり方で、時計や電池の帯の下まで画面を描いている。
どのページにも次の 3 つが要る (1 つでも欠けると、画面のいちばん上が別の色の板になり、アプリがその下から始まる)。

- `<meta name="viewport" content="..., viewport-fit=cover">`
- `<meta name="apple-mobile-web-app-capable" content="yes">` と
  `<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">`
- 上の安全域を空ける `env(safe-area-inset-top)` (site.css の `#app` と `body::before`、タイトル画面の `.waku`)

**iOS はホーム画面に追加したときの設定を覚えている。** これを変えたら、アイコンを一度消して追加し直さないと効かない。
