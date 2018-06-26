---
title: shutdownService
keywords: api
sidebar: api_sidebar
permalink: shutdownService.html
folder: api
toc: false
---


サービスのシャットダウン



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :----------------: | :-----: | :-----------: | :---------------: | --------------------- |
|         id         | 整数値 |     true      |      *null*       | サービスID |



## API Call テンプレート

```
shutdownService id=<serviceId>
```



### サンプル API Call

```
shutdownService id=5
```

この場合idが5のサービスをシャットダウンします



### JSONのSuccess Response

```
{
"data":{
    "acceptedConnectionsCount":0,
    "appId":1,
    "appName":"evostreamms",
    "clustering":true,
    "droppedConnectionsCount":0,
    "enabled":true,
    "id":5,
    "ip":"127.0.0.1",
    "port":1936,
    "protocol":"inboundRtmp",
    "sslCert":"",
    "sslKey":""
    },
"description":"Service 5 removed",
"status":"SUCCESS"
}
```

#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - acceptedConnectionsCount – サービスを使用するアクティブな接続数
  - appId – サービスにリンクするアプリケーションID
  - appName – サービスにリンクするアプリケーション名
  - droppedConnectionsCount – ドロップした接続数
  - enabled - サービスが有効なら**true**、 そうでなければ **false**
  - id = サービスID
  - ip = サービスにバインドされたIPアドレス
  - port – サービスにバインドされたポート
  - protocol – サービスにバインドされたプロトコル
  - sslCert – SSL証明書
  - sslKey – SSL証明書鍵

- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [createService](createService.html)
- [enableService](enableService.html)
- [listServices](listServices.html)
- [acceptors](userguide_configlua.html#acceptors)