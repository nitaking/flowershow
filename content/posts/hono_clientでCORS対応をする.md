---
tags:
  - posts
  - rpc
  - hono
  - cors
title: hono_clientでCORS対応をする
---
honoで`hono/client`を利用したRPCモードでのクライアント通信を実装していたところ、CORS対応にて調べた内容。

#### [[hono]]: CORS設定

> https://hono.dev/docs/middleware/builtin/cors

```ts
app.use(
	"*",
	cors({
		origin: "http://localhost:3000",
		allowHeaders: [
			"X-Custom-Header",
			"Upgrade-Insecure-Requests",
			"Content-Type",
			"Authorization",
		],
		allowMethods: ["POST", "GET", "OPTIONS"],
		maxAge: 600,
		credentials: true,
	}),
);
```

その場合のclientでは`init: {}`にてcredentials設定を行う。

```ts: client.ts
const _client = hc<ApiType>("http://localhost:5001", {
	headers: {
		"Content-Type": "application/json",
	},
	init: {
		credentials: "include",
	},
});

```

> https://github.com/orgs/honojs/discussions/2291
