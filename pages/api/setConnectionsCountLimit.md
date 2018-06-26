---
title: setConnectionsCountLimit
keywords: api
sidebar: api_sidebar
permalink: setConnectionsCountLimit.html
folder: api
toc: false
---

EMSが許可する同時接続数を設定するインターフェースです



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :----------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|       count        | 整数値 |   true    |    *null*     | 一度に接続を許可する最大値 CLI接続は影響をうけません |



## API Call テンプレート

```
setConnectionsCountLimit count=<count>
```



### サンプル API Call

```
setConnectionsCountLimit count=500
```

This sets the connection limit to 500.



### JSONのSuccess Response

```
{
"data":{
    “cuurent”:3
    "limit":500
},
"description":"Connection counters",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - current – 現在の同時接続数
  - limit – 最大同時接続数
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [getConnectionsCountLimit](getConnectionsCountLimit.html)
- [getConnectionsCount](getConnectionsCount.html)