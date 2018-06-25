---
title: listIngestPoints
keywords: api
sidebar: api_sidebar
permalink: listIngestPoints.html
folder: api
toc: false
---



インジェストポイントのリストを返します





## API パラメータ

パラメータはありません



## API Call テンプレート

```
listIngestPoints
```



### JSONのSuccess Response

```
{
"data":{
    "privateStreamName":"testIngestPoint",
    "publicStreamName":"testPublicStreamName"
},
"description":"Available ingest points",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data– ペアのリスト
  - privateStreamName –設定されたプライベートストリーム名
  - publicStreamName – 設定されたパブリックストリーム名
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- **hasIngestPoints** in config.lua should be **TRUE**


------

## 関連リンク

- [hasIngestPoints](userguide_configlua.html#hasingestpoints)


- [createIngestPoint](createIngestPoint.html)
- [removeIngestPoint](removeIngestPoint.html)
- [ingestpoints.xml](userguide_ingestpoints.html)