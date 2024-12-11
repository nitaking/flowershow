---
tags:
  - seed
  - web_framework
title: Remix
---

- [Remix Resource Page]([Remix Resources](https://remix.run/resources?category=templates))でスターターパックが豊富で

---

# 引用や調査
## Next.js vs [[Remix]]
#### 1. データフェッチとレンダリング手法
> • **Next.js**: 静的サイト生成（SSG）、サーバーサイドレンダリング（SSR）、クライアントサイドレンダリング（CSR）をサポートし、プロジェクトの要件に応じて適切なレンダリング手法を選択できます。 ([Qiita](https://qiita.com/IYA_UFO/items/d8eabb3152c8d1d7223c))
> 
> • **Remix**: 主にSSRを採用し、SSGはサポートしていません。その代わり、HTTPヘッダーのCache-Controlを活用してキャッシュ戦略を柔軟に設定できます。 ([Zenn](https://zenn.dev/steelydylan/articles/remix-nextjs-comparison))

#### **2. Web標準の活用**
> • **Next.js**: 独自の機能やAPIが多く、学習コストが高い場合があります。 ([Zenn](https://zenn.dev/noko_noko/articles/90ad5279dfdd1e))

> • **Remix**: Web標準APIを尊重し、フォーム送信にはFormDataを使用するなど、標準的な技術を活用しています。これにより、学習した知識が他のプロジェクトでも応用しやすい利点があります。 ([Zenn](https://zenn.dev/typebase_dev/articles/why-choose-remix))

#### **3. デプロイ環境と適応性**
> • **Next.js**: Vercelとの親和性が高く、Vercel上でのデプロイで多くの恩恵を受けられます。他の環境でも動作しますが、特定の機能はVercel上で最適化されています。 ([Zenn](https://zenn.dev/noko_noko/articles/90ad5279dfdd1e))

> • **Remix**: Express、AWS Lambda、Cloudflare Workersなど、多様な環境で動作するアダプターが提供されており、特定のプラットフォームに依存しない柔軟性があります。 ([Zenn](https://zenn.dev/steelydylan/articles/remix-nextjs-comparison))

#### **4. エラーハンドリングと開発者体験**

> • **Remix**: エラーや中断、競合状態を自動的に処理する機能が組み込まれており、開発者の負担を軽減します。 ([React Japan](https://react-japan.dev/blog/remix-vs-next))

> [!note] My Notes
>  NextはWeb標準から乖離しており、ベンダーロックインと学習コストの高さがネックとなっている。
>  
