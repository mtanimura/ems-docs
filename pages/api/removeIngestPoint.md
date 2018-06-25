---
title: removeIngestPoint
keywords: api
sidebar: api_sidebar
permalink: removeIngestPoint.html
folder: api
toc: false
---



RTMPインジェストポイントを削除します





## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :---------------: | :----: | :-------: | :-----------: | ---------------------------------------- |
| privateStreamName | 文字列 |   true    |    *null*     | `privateStreamName`に同定される削除されるインジェストポイント |



## API Call テンプレート

```
removeIngestPoint privateStreamName=<theIngestPoint>
```



### サンプル API Call

```
removeIngestPoint privateStreamName=testIngestPoint
```

### JSONのSuccess Response

```
{
"data":{
    "privateStreamName":"testIngestPoint",
    "publicStreamName":"testPublicStreamName"
},
"description":"Ingest point removed",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - privateStreamName – 削除されたインジェストポイントの`privateStreamName`
  - publicStreamName – 削除されたインジェストポイントの`publicStreamName`
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

-  config.luaの**hasIngestPoint**は**TRUE**である必要があります


------

## 関連リンク

- [hasIngestPoints](userguide_configlua.html#hasingestpoints)
- [createIngestPoint](createIngestPoint.html)
- [listIngestPoints](listIngestPoints.html)
- [ingestpoints.xml](userguide_ingestpoints.html)

