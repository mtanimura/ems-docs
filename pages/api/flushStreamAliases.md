---
title: flushStreamAliases
keywords: api
sidebar: api_sidebar
permalink: flushStreamAliases.html
folder: api
toc: false
---



ストリームの全エイリアスを無効化します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
flushStreamAliases
```



### JSONのSuccess Response

```
{
"data":null,
"description":"All aliases are flushed",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースするデータはありません
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- config.luaの**hasIngestPoints** は **TRUE**にする必要があります


------

## 関連リンク

- [hasStreamAliases](userguide_configlua.html#hasstreamaliases)
- [listStreamAliases](listStreamAliases.html)
- [removeStreamAlias](removeStreamAlias.html)
- [addStreamAliases](addStreamAlias.html)