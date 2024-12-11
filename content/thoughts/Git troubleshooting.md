---
tags:
  - troubleshooting
title: Git troubleshooting
---
# RPC failed; HTTP 400 curl 22 The requested URL returned error: 400 send-pack: unexpected 

`git push`時に発生。

発生したエラー内容:

```shell
RPC failed; HTTP 400 curl 22 The requested URL returned error: 400 send-pack: unexpected disconnect while reading sideband packet Total 158 (delta 9), reused 0 (delta 0), pack-reused 0 the remote end hung up unexpectedly
```

解消方法: push時のバッファサイズの上限を変更。

```shell
# バッファサイズを500MBに変更
git config --global http.postBuffer 524288000
```

### Resource
- [【備忘録】Git - push時のエラーの解消](https://zenn.dev/hiro8_hiro8/articles/d63b3bfbe2c86e)
