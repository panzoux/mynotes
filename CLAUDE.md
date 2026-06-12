# mynotes

GitHub Pages で公開している個人メモサイト。
URL: https://panzoux.github.io/mynotes/
Repo: https://github.com/panzoux/mynotes

## ショートコマンド

| 入力例 | 動作 |
|--------|------|
| `add: Gitのrebaseとは` | そのテーマでノートを新規作成してpush |
| `list` | 現在のノート一覧を表示 |
| `edit: sample` | 指定ノートを編集 |

## addコマンドの動作仕様

1. `notes/` 以下に英語スラッグ名の `.html` ファイルを作成
2. 内容はテーマについてわかりやすく説明（見出し・コード例など適宜）
3. `index.html` のリストの先頭に追記（日付は今日）
4. git add / commit / push まで実行する

## ファイル構成

- `index.html` — 一覧ページ（リストは `<ul id="note-list">` 内）
- `style.css` — 共通スタイル
- `notes/*.html` — 各ノート（`../style.css` を参照）

## ノートHTMLテンプレート

```html
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>TITLE - My Notes</title>
  <link rel="stylesheet" href="../style.css">
</head>
<body>
  <header>
    <h1><a href="../index.html" style="text-decoration:none;color:inherit;">My Notes</a></h1>
  </header>
  <main>
    <article>
      <h1>TITLE</h1>
      <div class="date">DATE</div>
      <!-- 本文 -->
    </article>
    <a class="back" href="../index.html">← 一覧に戻る</a>
  </main>
</body>
</html>
```

## index.htmlへの追記フォーマット

```html
<li><a href="notes/SLUG.html"><div class="title">TITLE</div><div class="date">DATE</div></a></li>
```
