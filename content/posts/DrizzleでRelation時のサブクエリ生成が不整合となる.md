---
tags:
  - seed
  - orm
  - drizzle
title: DrizzleでRelation時のサブクエリ生成が不整合となる
---
DrizzleはSQLクエリビルダーなので、オブジェクトにマッピングされない。flatにクエリ出力される。（SQLと同じだ）

[Drizzle Queries](https://orm.drizzle.team/docs/rqb)を使用した場合、オブジェクトにマッピングされる。その際はSQL上でjsonを整形した上でキャストされるので高速だが、nestした場合（a -> b -> c）にサブクエリが3階層となり、aliasが繋がらないSQL生成結果となってしまった。つまりうまくクエリ生成ができなかった。

そのため、[Aggregating results](https://orm.drizzle.team/docs/joins#aggregating-results) という形で集計を試みた。

- [【Drizzle ORM】JOINした結果をマッピングして集計する](https://pote-chil.com/posts/drizzleorm-join-aggregate)
- [Drizzle Team Community - Answer Overflow](https://www.answeroverflow.com/c/1043890932593987624)

しかし、こちらはインメモリ処理をするため、実行速度が遅く、150件程度でレスポンスタイムが250ms程度となってしまった。ローカルでこれなので実用に耐えられず、断念。

結局、Prismaで実装したところ、エラーなくレスポンスタイムも60ms程度に済んだ。

---
その際のPR内容

> 
> 実装にあたり、以下の問題を抱えました。
> ### Case: Drizzle/Query
> 
> 出力されたサブクエリでのエイリアスやスコープが参照できないスコープとなってしまい、SQLレベルで実行エラーとなってしまう。
> ### Case: Drizzle/Select
> 
> Queriesを使用せずにネストした形でSQLを実行するためにはjson構造をうまく定義する必要があり、クエリレベルでの対応は手修正が必要となる。  
> PostgreSQLのhelperなどは散見されたが、MySQLでのhelperは確認できず。
> 
> [gist.github.com/rphlmr/de869cf24816d02068c3dd089b45ae82](https://gist.github.com/rphlmr/de869cf24816d02068c3dd089b45ae82) _(too large to embed)_
> 
> また、[Aggregating results](https://orm.drizzle.team/docs/joins#aggregating-results) を試したが、こちらはマッピングが手動になるためバグリスクがあり、ランタイムでNode.js上で処理するためパフォーマンスが悪く、最終的なレスポンスタイムが200ms以上となったため、不採用。
> 
> ### Case: MikrORM / Kysely
> 
> MikroORMはTypeORM同様、Decoratorでの定義が必要であり、少し作業量が多いと見た。  
> また、Kyselyはより薄いSQL Query Builderであり、Drizzleと変わらないように思える or オブジェクトへのマッピングの対応可否が確認できなかった。
> 
> ### Case: Prisma
> 
> Prismaでのオブジェクトのマッピングは実装歴があるため試したところ、Drizzle/Queriesと同じようなインタフェースで実行できるようになった。  
> Drizzleとの違いは実際のQueryで、Json構造で取り扱わずに複数のクエリで実行されていることによる。
> 
> 最終的なレスポンスタイムも約60msと良好である。  
> そのため、この実装を適用する。
> 
