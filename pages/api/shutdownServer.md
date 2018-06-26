---
title: shutdownServer
keywords: api
sidebar: api_sidebar
permalink: shutdownServer.html
folder: api
toc: false
---

サーバープロセスを終了し、EMSを完全にシャットダウンします。２回コールする必要があり、一回目はパラメータなしで、シャットダウンキーの取得を行い、２回目でキー付きでコールすることで実際にEMSを終了させることができます。



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|      key       | 整数値 |   true    |    *null*     | サーバーシャットダウンキー。キー無しでshutdownServerがコールされるとキーの取得を行えます。改めてキー付きでコールしてサーバーをシャットダウンできます |



## API Call テンプレート

```
shutdownServer
```

This will send a key in response



### サンプル API Call

```
{
"data":{
    "key":"GCY6IXniMf6NDOxY"
},
"description":"Call shutdownserver again with the provided key",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - key – `shutdownServer`の後に続けて使用する必要があるキー


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**





**サーバーをシャットダウンするには、同コマンドを与えられたキーパラメータ付きでコールしてください:**

```
shutdownServer key=GCY6IXniMf6NDOxY
```

コマンド送信後は接続は終了します


