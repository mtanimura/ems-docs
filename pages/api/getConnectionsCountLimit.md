---
title: getConnectionsCountLimit
keywords: api
sidebar: api_sidebar
permalink: getConnectionsCountLimit.html
folder: api
toc: false
---


同時接続数制限を返します。EMSインスタンスが許可する最大接続数





## API パラメータ

パラメータはありません



## API Call テンプレート

```
getConnectionsCountLimit
```



### JSONのSuccess Response

```
{
"data":{
    “cuurent”:3
    "limit":0
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

- [setConnectionsCountLimit](setConnectionsCountLimit.html)
- [getConnectionsCount](getConnectionsCount.html)

