---
title: resetTotalFdCounters
keywords: api
sidebar: api_sidebar
permalink: resetTotalFdCounters.html
folder: api
toc: false
---

接続カウンタから累計総数をリセット



## API パラメータ

パラメータはありません



## API Call テンプレート

```
resetTotalFdCounters
```



### JSONのSuccess Response

```
{
"data":null,
"description":"Total counters are cleared",
"status":"SUCCESS"
}
```



#### JSON Response

The JSON response contains the following details:

- data – パースするデータはありません
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## 関連リンク

- [resetMaxFdCounters](resetMaxFdCounters.html)