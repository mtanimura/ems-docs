---
title: listStreamsIds
keywords: api
sidebar: api_sidebar
permalink: listStreamsIds.html
folder: api
toc: false
---

**アクティブ**なストリームのIDリスト取得



## API パラメータ

パラメータはありません



## API Call テンプレート

```
listStreamsIds
```



### JSONのSuccess Response

```
{
"data":[205,206,207],
"description":"Available stream IDs",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – アクティブなストリームのID(整数値)配列を含みます
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- IDは時間とともに変わることがあります


------

## 関連リンク

- [listStreams](api_listStreams.html)