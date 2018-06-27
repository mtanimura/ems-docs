---
title: createService
keywords: api
sidebar: api_sidebar
permalink: createService.html
folder: api
toc: false
---


新しいサービスを作成します


## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :----------------: | :----: | :-----------: | :---------------: | ---------------------------------- |
|         ip         | 文字列 |     true      |      *null*       | バインドするIPアドレス |
|        port        | 文字列 |     true      |      *null*       | バインドするポート |
|      protocol      | 文字列 |     true      |      *null*       | バインドするプロトコル・スタック名 |
|      sslCert       | 文字列 |     false     |      *null*       | 使用されるSSL証明書 |
|       sslKey       | 文字列 |     false     |      *null*       | 使用されるSSL証明書鍵 |



## API Call テンプレート

```
createService ip=<ipAddress> port=<portNumber> protocol=<protocolName>
```



### サンプル API Call

```
createService ip=0.0.0.0 port=9556 protocol=inboundRtmp
```

ポート**9556** を使用し、**0.0.0.0**ipからアクセス可能な**inboundRtmp**サービスを作成します



### JSONのSuccess Response

```
{
"data":{
    "acceptedConnectionsCount":0,
    "appId":1,
    "appName":"evostreamms",
    "droppedConnectionsCount":0,
    "enabled":true,
    "id":974,
    "ip":"0.0.0.0",
    "port":1234,
    "protocol":"inboundRtmp"
    },
"description":"Service created",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - acceptedConnectionsCount – サービスを利用しているアクティブな接続すう
  - appId – サービスを利用するアプリケーションID
  - appName – サービスを利用するアプリケーション名
  - droppedConnectionsCount – ドロップした接続数
  - enabled - サービスが有効なら**true** 、そうでなければ **false**
  - id = サービスID
  - ip = サービスにバインドされたIPアドレス
  - port – サービスにバインドされたポート
  - protocol – サービスにバインドされたプロトコル
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- 作成したサービスはconfig.luaには書き込まれません


------

## 関連リンク

- [enableService](enableService.html)
- [listServices](listServices.html)
- [shutdownService](shutdownService.html)
- [acceptors](userguide_configlua.html#acceptors)