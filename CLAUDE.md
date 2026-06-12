# mynotes

GitHub Pages で公開している個人メモサイト。
URL: https://panzoux.github.io/mynotes/
Repo: https://github.com/panzoux/mynotes

---

## ガードレール

- **git push は絶対に自動実行しない。** ファイル編集・git add・git commit までを行い、必ずユーザーに差分確認を促してから push を待つ。
- 秘匿情報（APIキー・パスワード等）は `.gitignore` により管理外。JSON/YAML/YML/ENV ファイルはコミットしない。

---

## ショートコマンド

| 入力 | 動作 |
|------|------|
| `追加: Gitのrebaseとは` / `add: what is git rebase` | ノート新規作成 → commit まで（push はユーザー確認後） |
| `一覧` / `list` | 現在のノートファイル一覧を表示 |
| `編集: sample` / `edit: sample` | 指定ノートを編集 |

---

## addコマンドの動作仕様

1. テーマを調査し、**わかりやすいHTML記事**を生成する
   - 見出し・本文・コード例・図解（SVGまたは `<figure><img>`）を適宜使う
   - 有用な画像URL（公式ドキュメント・Wikimedia等、信頼性の高いもの）があれば `<figure>` で挿入
2. タグを **2〜4個** 自動付与（内容から判断）
3. `notes/` 以下に英語スラッグ名の `.html` を作成
4. `index.html` のリスト先頭に追記（`data-tags` 属性にタグをカンマ区切りで記載）
5. `git add` → `git commit` まで実行し、差分確認を促す（**push しない**）

---

## ファイル構成

- `index.html` — 一覧ページ（タグフィルター付き）
- `style.css` — 共通スタイル
- `notes/*.html` — 各ノート
- `.gitignore` — 秘匿ファイル除外設定

---

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
      <div class="source">参考: <a href="SOURCE_URL" target="_blank">SOURCE_TITLE</a></div>
      <!-- 本文: 見出し・コード・figure/figcaptionなどを使ってわかりやすく -->
    </article>
    <a class="back" href="../index.html">← 一覧に戻る</a>
  </main>
</body>
</html>
```

## index.html への追記フォーマット

```html
<li data-tags="TAG1,TAG2"><a href="notes/SLUG.html"><div class="title">TITLE</div><div class="date">DATE</div><div class="tags"><span class="tag">TAG1</span><span class="tag">TAG2</span></div></a></li>
```
