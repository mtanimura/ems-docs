---
title: getConnectionInfo
keywords: api
sidebar: api_sidebar
permalink: getConnectionInfo.html
folder: api
toc: false
---


接続に関する情報を返します




## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :----------------: | :-----: | :-----------: | :---------------: | ---------------------------------------- |
|         id         | 整数値 |     true      |      *null*       | 接続のuniqueId 通常は`listStreamsIds`で返される値 |



## API Call テンプレート

```
getConnectionInfo id=<id>
```



### サンプル API Call

```
getConnectionInfo id=144
```



### JSONのSuccess Response

```
{
    "data":{
        "carrier":null,
        "stack":[
            {
                "applicationId":1,
                "creationTimestamp":1338633696196.6460,
                "id":144,
                "isEnqueueForDelete":false,
                "queryTimestamp":1338658491380.7349,
                "type":"TMR"
            }
        ]
    },
    "description":"Connection information",
    "status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - carrier - 接続に関する詳細情報
  - stack - 接続を使用している内部リソースに関する情報
    - applicationId - 接続を使用している内部アプリケーションID
    - creationTimeStamp - アプリケーションが接続の使用を開始した時間(UNIX秒)
    - Id - スタック関係のユニークID
    - isEnqueForDelete - 削除に使用する内部フラグ
    - queryTimeStamp - データがクエリーされた時間(UNIX秒)
    - type - アプリケーションの接続の使用についての記述子
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [listConnections](listConnections.html)