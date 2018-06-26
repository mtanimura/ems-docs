---
title: pushMetadata
keywords: api
sidebar: api_sidebar
permalink: pushMetadata.html
folder: api
toc: false
---

JSONメタデータオブジェクトが送られるアウトバウンドVmf TCPストリームを開きます



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
| localStreamName | 文字列  |   true    |    *null*     | 関連するメタデータがおくられるストリーム名 |
|      type       | 文字列  |   false   |      vmf      | プッシュストリームタイプ |
|       ip        | 文字列  |   false   |   127.0.0.1   | プッシュ先IPアドレス                |
|      port       | 整数値 |   false   |     8110      | プッシュ先ポート                        |



## API Call テンプレート

```
pushMetadata localStreamName=testpullStream ip=<ipAddress> port=<portNumber>
```



### サンプル API Call

```
pushMetadata localStreamName=testpullStream ip=192.168.0.1 port=8110
```



### JSONのSuccess Response

```
{
   "data":{
      "applicationName":"evostreamms",
      "ip":"192.168.0.1",
      "keepAlive":true,
      "localStreamName":"testpullStream",
      "name":"evostreamms",
      "port":8110,
      "protocol":"outboundVmf",
      "streamName":"testpullStream",
      "type":"vmf"
   },
   "description":"Launched Metadata Push Stream",
   "status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - applicationName – EMS (evostreamms)
  - ip – プッシュ先IPアドレス
  - keepAlive – 再起動後に有効化されるかどうか
  - localStreamName – 関連メタデータが送られるストリーム名
  - name – アプリケーション名(evostreamms)
  - port – プッシュ先ポート
  - protocol – ストリームタイプ
  - streamName – 関連メタデータが送られるストリーム名
  - type – ストリームタイプ


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [getMetadata](getMetadata.html)
- [shutdownMetadata](shutdownMetadata.html)