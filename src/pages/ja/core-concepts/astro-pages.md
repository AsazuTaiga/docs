---
layout: ~/layouts/MainLayout.astro
title: ページ
description: Astroページの紹介
i18nReady: true
---

**ページ**は、Astroプロジェクトの`src/pages/`サブディレクトリにあるファイルです。Webサイトの各ページのルーティングやデータ読み込み、全体的なページレイアウトを処理する役割を担っています。

## サポートしているページファイル

Astroは`src/pages/`ディレクトリの次のファイルタイプをサポートしています。
- [`.astro`](#astroページ)
- [`.md`](#markdownmdxページ)
- `.mdx` （[MDXインテグレーションがインストール](/ja/guides/integrations-guide/mdx/#installation)されている場合）
- [`.html`](#htmlページ)
- [`.js`/`.ts`] （[エンドポイント](/ja/core-concepts/endpoints/)として）

## ファイルベースルーティング

Astroは、**ファイルベースルーティング**と呼ばれるルーティング手法を採用しています。 `src/pages/`ディレクトリの各ファイルはそのファイルパスに基づいたエンドポイントになります。

ページ間のリンクを張るには、HTMLの[`<a>`要素](https://developer.mozilla.org/ja/docs/Web/HTML/Element/a)をコンポーネントテンプレートに記述してください。

📚 [Astroのルーティング](/ja/core-concepts/routing/)について詳しくみる。

## Astroページ

Astroページは`.astro`拡張子を使い[Astroコンポーネント](/ja/core-concepts/astro-components/)と同じ機能を持ちます。

```astro
---
// 例: src/pages/index.astro
---
<html lang="ja">
  <head>
    <title>ホームページ</title>
  </head>
  <body>
    <h1>私のホームページへようこそ！</h1>
  </body>
</html>
```

すべてのページで同じHTML要素を繰り返すことを避けるために、共通の `<head>` と `<body>` 要素を独自の[レイアウトコンポーネント](/ja/core-concepts/layouts/)に移動できます。レイアウトコンポーネントはいくつでも使えます。

```astro {3} /</?MySiteLayout>/
---
// 例: src/pages/index.astro
import MySiteLayout from '../layouts/MySiteLayout.astro';
---
<MySiteLayout>
  <p>レイアウトに包まれたコンテンツ！</p>
</MySiteLayout>
```

📚 Astroの[レイアウトコンポーネント](/ja/core-concepts/layouts/)について詳しくみる。

## Markdown/MDXページ

Astroは `/src/pages/` にあるMarkdown (`.md`) ファイルも、最終的なWebサイトのページとして扱います。もし[MDXインテグレーションがインストールされている](/ja/guides/integrations-guide/mdx/#installation)場合、MDX(`.mdx`)ファイルも同じように扱われます。これらは一般的に、ブログの投稿やドキュメントのような、テキストを多用するページに使用されます。

ページレイアウトは[Markdownファイル](#markdownmdxページ)に対して特に有効です。Markdownファイルは特別な `layout`というfront-matterプロパティを使用して、Markdownコンテンツを `<html>...</html>` ページドキュメントにラップする [レイアウトコンポーネント](/ja/core-concepts/layouts/)を指定できます。

```md {3}
---
# 例: src/pages/page.md
layout: '../layouts/MySiteLayout.astro'
title: 'Markdownページ'
---
# タイトル

これは**Markdown**で書かれたページです。
```

📚 Astroの[Markdown](/ja/guides/markdown-content/)について詳しくみる。

## HTMLページ

`.html`拡張子のついたファイルを`src/pages`内に置くことができ、直接サイトのページとして使用されます。[HTMLコンポーネント](/ja/core-concepts/astro-components/#htmlコンポーネント)ではAstroの主要機能の一部がサポートされていないことに注意してください。

## カスタム404エラーページ

カスタムの404エラーページを作成するには、`src/pages`に `404.astro` または `404.md` ファイルを作成します。

これは `404.html` ページにビルドされます。ほとんどの[デプロイサービス](/ja/guides/deploy/)はこのファイルを見つけて使用します。

