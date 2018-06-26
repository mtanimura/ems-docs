---
title: listMetadataListeners
keywords: api
sidebar: api_sidebar
permalink: listMetadataListeners.html
folder: api
toc: false
---

Returns the list of all metadata listeners created either through the config.lua or through the `addMetadataListener` API.



## API パラメータ

This function has no parameters.



## API Call テンプレート

```
listMetadataListeners
```


### JSONのSuccess Response

```
{
"data":{
"listeners":[
     {
      "acceptor":{
        "acceptedConnectionsCount":0,
          "acceptor":{
            "acceptedConnectionsCount":0,
            "acceptor":{
              "acceptedConnectionsCount":0,
              "appId":1,
              "appName":"evostreamms",
              "droppedConnectionsCount":0,
              "enabled":true,
              "id":1169,
              "ip":"0.0.0.0",
              "localStreamName":"meta",
              "port":3535,
              "protocol":"inboundJsonMeta"
               },
          "appId":1,
          "appName":"evostreamms",
          "droppedConnectionsCount":0,
          "enabled":true,
          "id":25,
          "ip":"0.0.0.0",
          "localStreamName":"meta",
          "operationType":11,
          "port":3535,
          "protocol":"inboundJsonMeta"
          },
      "appId":1,
      "appName":"evostreamms",
      "droppedConnectionsCount":0,
      "enabled":true,
      "id":25,
      "ip":"0.0.0.0",
      "localStreamName":"meta",
      "operationType":11,
      "port":3535,
      "protocol":"inboundJsonMeta"
      },
    "configId":13,
    "id":25,
    "ip":"0.0.0.0",
    "localStreamName":"meta",
    "operationType":11,
    "port":3535,
    "protocol":"inboundJsonMeta"
    },
    {
    "acceptedConnectionsCount":0,
    "appId":1,
    "appName":"evostreamms",
    "droppedConnectionsCount":0,
    "enabled":true,
    "id":11,
    "ip":"0.0.0.0",
    "port":8100,
    "protocol":"inboundJsonMeta",
    "sslCert":"",
    "sslKey":""
    }
  ]
},
"description":"Listing all the metadata listeners",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – 各プロトコルについて下記の情報を提供します
  - acceptedConnectionsCount - サービスを利用するアクティブな接続数
  - appId - サービスを使用するアプリケーションID
  - appName - サービスを使用するアプリケーション
  - droppedConnectionsCount - ドロップした接続数
  - enabled - サービスが有効の場合は`true`、そうでなければ `false`
  - id - サービスのID
  - ip - サービスが使用するipアドレス
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

- [addMetadataListener](addMetadataListener.html)
- [createService](createService.html)
- [enableService](enableService.html)
- [shutdownService](shutdownService.html)
- [acceptors](userguide_configlua.html#acceptors)