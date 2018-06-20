---
title: resetMaxFdCounters
keywords: api
sidebar: api_sidebar
permalink: resetMaxFdCounters.html
folder: api
toc: false
---



接続カウンタから最大値またはhigh-water-markをリセットする





## API パラメータ

パラメータはありません




## API Call テンプレート

```
resetMaxFdCounters
```



### JSONのSuccess Response

```
{
"data":null,
"description":"Max counters are cleared",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースするデータはありません
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## 関連リンク

- [resetTotalFdCounters](resetTotalFdCounters.html)