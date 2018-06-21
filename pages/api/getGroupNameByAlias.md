---
title: getGroupNameByAlias
keywords: api
sidebar: api_sidebar
permalink: getGroupNameByAlias.html
folder: api
toc: false
---



エイリアス名が与えられたグループ名を返します





## API パラメータ



| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :----: | :-------: | :-----------: | --------------------------------------- |
|   aliasName    | 文字列 |   true    |    *null*     | グループ名のエイリアス |



## API Call テンプレート

```
getGroupNameByAlias aliasName=<groupAliasName>
```



### サンプル API Call

```
getGroupNameByAlias aliasName=testGroupAlias
```



### JSONのSuccess Response

```
"data":{
	"aliasName":"testGroupAlias",
	"cliProtocolId":97,
	"edges":[ ],
	"edgesCount":0,
	"groupName":"testAliasGroup",
	"lastUpdate":1442374870,
	"operation":"getGroupNameAlias",
	"result":true,
	"uniqueRequestId":4
},
"description":"Group name",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - aliasName – `localStreamName`に対するエイリアス
  - groupName – エイリアスが適用されたグループ名
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

-  config.luaの**hasStreamAliases**は**TRUE**である必要があります

------

## 関連リンク

- [hasGroupNameAliases](userguide_webconfig.html#hasgroupnamealiases)
- [addGroupNameAlias](addGroupNameAlias.html)
- [listGroupNameAliases](listGroupNameAliases.html)
- [removeGroupNameAliases](removeGroupNameAliases.html)
- [flushGroupNameAliases](flushGroupNameAliases.html)

