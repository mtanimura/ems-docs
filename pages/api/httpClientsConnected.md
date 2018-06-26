---
title: httpClientsConnected
keywords: api
sidebar: api_sidebar
permalink: httpClientsConnected.html
folder: api
toc: false
---


EWSを利用している全クライエント数を返します



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :----------------: | :----: | :-----------: | :---------------: | ---------------------------------------- |
|     groupName      | 文字列 |     false     |      *null*       | 特定のグループ名 このパラメータが指定されている場合、当該グループに属するストリームを再生しているクライエント数を返します |



## API Call テンプレート

```
httpClientsConnected
```



### サンプル API Call

```
httpClientsConnected
```

```
httpClientsConnected groupName=MyGroupStream
```



### JSONのSuccess Response

```
{
"data":{
    "groupName":"",
    "httpStreamingSessionsCount":2
},
"description":"Number of clients connected to Evostream Web Server",
"status":"SUCCESS"
}
```

```
{
"data":{
    "groupName":"MyGroupStream",
    "httpStreamingSessionsCount":1
},
"description":"Number of clients connected to Evostream Web Server under groupname: MyGroupStream",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - groupName – クライエントが接続するグループ名
  - httpStreamingSessionsCount – 接続クライエント数
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [clientsConnected](clientsConnected.html)