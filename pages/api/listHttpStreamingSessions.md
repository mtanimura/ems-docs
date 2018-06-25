---
title: listHttpStreamingSessions
keywords: api
sidebar: api_sidebar
permalink: listHttpStreamingSessions.html
folder: api
toc: false
---

アクティブなHTTPストリーミングセッションをリストします



## API パラメータ

パラメータはありません



## API Call テンプレート

```
listHttpStreamingSessions
```



### JSONのSuccess Response

```
{
  "data": [
    {
    "clientIP": "127.0.0.1",
    "elapsedTime": 33,
    "sessionId": 1,
    "startTime": "2014-12-17T18-31-13",
    "targetFolder": "C:\\xampp\\htdocs\\hls_group\\mystream"
    }
  ],
  "description":"Currently open HTTP streaming sessions",
  "status":"SUCCESS"
}
```



#### JSON Response

- data – パースすべきデータ
  - clientIP – 接続クライエントのIPアドレス
  - sessionId – 内部セッションID
  - startTime – セッション開始時のタイムスタンプ
  - elapsedTime – セッション開始から経過時間
  - targetFolder – HTTPストリーミングでソースとして使用されているフォルダ

- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## 関連リンク

- [httpClientsConnected](httpClientsConnected.html)