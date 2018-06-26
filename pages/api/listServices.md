---
title: listServices
keywords: api
sidebar: api_sidebar
permalink: listServices.html
folder: api
toc: false
---

利用可能なサービスのリストを返します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
listServices
```


### JSONのSuccess Response

```
{
"data":[
    {
    "acceptedConnectionsCount":1,
    "appId":1,
    "appName":"evostreamms",
    "droppedConnectionsCount":0,
    "enabled":true,
    "id":1,
    "ip":"127.0.0.1",
    "port":1112,
    "protocol":"inboundJsonCli",
    "sslCert":"",
    "sslKey":"",
    "useLengthPadding":true
    },
    --content removed for clarity
    {
    --content removed for clarity
    "protocol":"inboundLiveFlv",
    "sslCert":"",
    "sslKey":"",
    "waitForMetadata":true
    },
    --content removed for clarity
    ],
"description":"Available services",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – 各プロトコルで下記の情報を提供します
  - acceptedConnectionsCount – サービスを使用するアクティブな接続数
  - appId – サービスにリンクするアプリケーションID
  - appName – サービスにリンクするアプリケーション名
  - droppedConnectionsCount – ドロップした接続数
  - enabled - サービスが有効なら**true**、 そうでなければ **false**
  - id = サービスID
  - ip = サービスにバインドされたIPアドレス
  - port – サービスにバインドされたポート
  - protocol – サービスにバインドされたプロトコル
  - sslCert – SSL証明書 (いくつかのプロトコルのみ)
  - sslKey – SSL証明書鍵 (いくつかのプロトコルのみ)
  - useLengthPadding – paddingが有効なら**true**、そうでなければ **false** (いくつかのプロトコルのみ)
  - waitForMetadata – メタデータが必須なら**true** そうでなければ **false** (いくつかのプロトコルのみ) 
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [createService](createService.html)
- [enableService](enableService.html)
- [shutdownService](shutdownService.html)
- [acceptors](userguide_configlua.html#acceptors)