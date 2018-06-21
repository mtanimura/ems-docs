---
title: addGroupNameAlias
keywords: api
sidebar: api_sidebar
permalink: addGroupNameAlias.html
folder: api
toc: false
---



グルーム名に二次的な名前を付けます。エイリアスがいったん作成されるとグループ名はHTTPリクエストで使用できなくなります。またエイリアスが一度使用されると(クライエントのリクエスト)、そのエイリアスは削除されます。エイリアス機能はソースストリームの保護・隠蔽に使用するようデザインされています。





## API パラメータ


| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :----: | :-------: | :-----------: | --------------------------------------- |
|   groupName    | 文字列 |   true    |    *null*     | オリジナルのグループ名 |
|   aliasName    | 文字列 |   true    |    *null*     | グループ名エイリアス |



## API Call テンプレート

```
addGroupNameAlias groupName=<groupName> aliasName=<groupAliasName>
```



### サンプル API Call

```
addGroupNameAlias groupName=testAliasGroupName aliasName=testGroupAlias
```



### JSONのSuccess Response

```
"data":{
	"aliasName":"testGroupAlias",
	"cliProtocolId":97,
	"edges":[
	],
	"edgesCount":0,
	"groupName":"testAliasGroupName",
	"lastUpdate":1442374870,
	"operation":"addGroupNameAlias",
	"result":true,
	"uniqueRequestId":2
},
"description":"Alias applied to group name",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - aliasName – `localStreamName`に対するエイリアス
  - groupName – エイリアスが適用されているグループ名
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## Notes

- webconfig.luaの**hasGroupNameAliases**は**TRUE**に設定する必要があります

------

## 関連リンク

- [hasGroupNameAliases](userguide_webconfig.html#hasgroupnamealiases)
- [listGroupNameAliases](listGroupNameAliases.html)
- [removeGroupNameAliases](removeGroupNameAliases.html)
- [flushGroupNameAliases](flushGroupNameAliases.html)
