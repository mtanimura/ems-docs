---
title: addMetadataListener
keywords: api
sidebar: api_sidebar
permalink: addMetadataListener.html
folder: api
toc: false
---

ランタイムで新規acceptorを指定します



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|      port       | 整数値|   true    |    *null*     | バインドされるポート |
|       ip        | 文字列  |   false   |    0.0.0.0    | バインドされるipアドレス |
| localStreamName | 文字列  |   false   |   0 ~ 0 ~ 0   | バインドされるlocalStreamName デフォルト値(0 ~ 0 ~ 0) は全てのストリームに適用を意味します。



## API Call テンプレート

```
addMetadataListener port=3535
```



### サンプル API Call

```
addMetadataListener port=3535 localstreamname=meta
```



### JSONのSuccess Response

```
{
"data":{
"acceptedConnectionsCount":0,
"appId":1,
"appName":"evostreamms",
"droppedConnectionsCount":0,
"enabled ":true,
"id":1169,
"ip":"0.0.0.0",
"localStreamName":"meta",
"port":3535,
"protocol":"inboundJsonMeta"
},
"description":"Metadatalistener created",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - acceptedConnectionsCount - サービスを利用するアクティブな接続数
  - appId - サービスを使用するアプリケーションID
  - appName - サービスを使用するアプリケーション
  - droppedConnectionsCount - ドロップした接続数
  - enabled - サービスが有効の場合は`true`、そうでなければ `false`
  - id - サービスのID
  - ip - サービスが使用するipアドレス
  - localStreamName - 関連メタデータが送られるストリーム名Name of the stream to which the associated metadata will be sent
  - port - serviceが使用するポート
  - protocol - serviceが使用するプロトコル

- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## 関連リンク

- [mediaStorage](userguide_confuglua.html#mediastorage)
- [listStorage](listStorage.html)
- [removeStorage](removeStorage.html)

