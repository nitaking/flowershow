---
tags:
  - seed
  - typescript
title: process.env
---
## process.envを利用した際の型定義とアクセス

`config.ts`としてexport先をラップすることが多いです。process.envはoptionalでvalidationかけたいシーンがあったり、string以外にcastしたいシーンがあるためです。
また、使う側はprocess.envであるかどうかは関心事ではないので、infraから依存をなくすためです。

```ts
type Config = {};

export const config = {

} satisfies Config as const;
```

