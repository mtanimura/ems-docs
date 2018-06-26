---
title: clientsConnected
keywords: api
sidebar: api_sidebar
permalink: clientsConnected.html
folder: api
toc: false
---


EMSを利用中の全クライエント数を返します



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :----------------: | :----: | :-----------: | :---------------: | ---------------------------------------- |
|  localStreamName   | 文字列 |     false     |      *null*       | 特定のストリーム名。このパラメータが指定されている場合コマンドは特定のストリームに接続しているクライエント数を返します |



## API Call テンプレート

```
clientsConnected
```



### サンプル API Call

```
clientsConnected
```

```
clientsConnected localStreamName=testpullStream
```



### JSONのSuccess Response

```
{
"data":{
    "outboundCount":3
},
"description":"EMS outbound client connections count",
"status":"SUCCESS"
}
```

```
{
"data":{
		"outboundCount":1
},
"description":"EMS outbound client connections count for the corresponding localstreamname: testpullStream",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - outboundCount – クライエント接続数
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## 関連リンク

- [httpClientsConnected](httpClientsConnected.html)

