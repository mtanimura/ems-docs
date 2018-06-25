---
title: removeStreamAlias
keywords: api
sidebar: api_sidebar
permalink: removeStreamAlias.html
folder: api
toc: false
---



ストリームエイリアスを削除します



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :----: | :-------: | :-----------: | ------------------- |
|   aliasName    | 文字列 |   true    |    *null*     | 削除するエイリアス |



## API Call テンプレート

```
removeStreamAlias aliasName=<aliasName>
```



### サンプル API Call

```
removeStreamAlias aliasName=testAlias
```

### JSONのSuccess Response

```
{
"data":{
	"aliasName":"testAlias"
},
"description":"Alias removed",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - ​	aliasName – 削除されたストリームエイリアス
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## Notes

- config.luaの**hasStreamAliases**は**TRUE**である必要があります


------

## 関連リンク

- [hasStreamAliases](userguide_configlua.html#hasstreamaliases)
- [addStreamAlias](addStreamAlias.html)
- [listStreamAliases](listStreamAliases.html)
- [flushStreamAliases](flushStreamAliases.html)