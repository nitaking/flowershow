---
tags:
  - posts
  - hono
title: HonoでStaticAssets設定するときの注意点
---
[[hono]]で [Serve static files​](https://hono.dev/docs/getting-started/nodejs#serve-static-files) を参照して設定していたところ、少しハマっていたのでメモ。

```typescript
// /src/index.ts

const app = new Hono().basePath("/api");
app.use("/static/[]()*", serveStatic({ root: "./" }));
```

```bash
├── src
│   ├── domain
│   ├── infrastructure
│   ├── routes
│   └── use-case
└── static
    └── images
```

このような状況で`static/image/file.xxx`がNot Foundになって困っていました。

どうやら`basePath`がstaticPathにも影響するらしく、staticPathのmiddlewareの設定以前にbasePath設定があると影響するようでした。

```typescript
// /src/index.ts

const app = new Hono();
app.use("/static/*", serveStatic({ root: "./" }));
app.basePath("/api");
```

このようにmiddleware以降にbasePath設定をすることでstaticPathへのアクセスが適切にできるようになりました。

`serveStatic`のrootの対象がどこからなのかわからないこともあって、結構時間が溶けました。。。

ちなみに、

> - Root path, relative to current working directory from which the app was started. Absolute paths are not supported.
>     
>     [https://github.com/honojs/node-server/blob/590fe6cef8a795ea10c300033387f13ed31e144f/src/serve-static.ts#L9](https://github.com/honojs/node-server/blob/590fe6cef8a795ea10c300033387f13ed31e144f/src/serve-static.ts#L9)
>     

コードのコメント上にある通り、root pathは`index.ts`（ここでいう`src/`パス）のディレクトリではなく、プロセスの起動しているディレクトリであるproject root pathになるので注意。
