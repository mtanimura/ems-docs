---
title: createIngestPoint
keywords: api
sidebar: api_sidebar
permalink: createIngestPoint.html
folder: api
toc: false
---


RTMPインジェストポイントを作成します。EMSにプッシュされるストリームはインジェストポイントの`privateStreamName`に一致するターゲットストリーム名を持っている必要があります。



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :---------------: | :----: | :-------: | :-----------: | ---------------------------------------- |
| privateStreamName | 文字列 |   true    |    *null*     | RTMPターゲットストリーム名がマッチすべき名前 |
| publicStreamName  | 文字列 |   true    |    *null*     | `privateStreamName`にプッシュされるストリームへアクセスするために使用される名前。`publicStreamName`は`localStreamName`ストリームになります |



## API Call テンプレート

```
createIngestPoint privateStreamName=<theIngestPoint> publicStreamName=<publicStreamName>
```



### サンプル API Call

```
createIngestPoint privateStreamName=testIngestPoint publicStreamName=testPublicStreamName
```



### JSONのSuccess Response

```
{
"data":{
    "privateStreamName":"testIngestPoint",
    "publicStreamName":"testPublicStreamName"
},
"description":"Ingest point created",
"status":"SUCCESS"
}
```



#### JSON Response

The JSON response contains the following details:
JSON responseは以下を含みます:

- data – パースすべきデータ
  - privateStreamName –設定されたprivateStreamName
  - publicStreamName – 設定されたpublicStreamName
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

-  config.luaの**hasIngestPoint** は**TRUE**である必要があります
-  ストリーム再生には`publicStreamName`を使用してください

------

## 関連リンク

- [hasIngestPoints](userguide_configlua.html#hasingestpoints)
- [listIngestPoints](listIngestPoints.html)
- [removeIngestPoint](removeIngestPoint.html)
- [ingestpoints.xml](userguide_ingestpoints.html)
