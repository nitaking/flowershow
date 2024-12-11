---
tags:
  - seed
title: DB・Table設計
---

- PostgreSQLの場合、PKやidは`UUID`を設定する
- MySQLの場合、原則として、テーブルの Primary Key にはサロゲートキーを使用する。
	- サロゲートキーは　unsigned value で定義し、自動的にインクリメントされるものを使用する
	- サロゲートキー（代理キー）
		- [DB設計　サロゲートキーとナチュラルキー #MySQL - Qiita](https://qiita.com/masapiko/items/05c393379c2eb42c86f5)

---

- [MySQL DB レビューで使用しているガイドライン](https://zenn.dev/moaikids/articles/14bc88c8bc9492)
- [サロゲートキーの扱いに終止符を打ちたい - 日々量産](https://ryozi.hatenadiary.jp/entry/2024/05/27/181448#%E3%82%B5%E3%83%AD%E3%82%B2%E3%83%BC%E3%83%88%E3%82%AD%E3%83%BC)
