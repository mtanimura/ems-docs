---
title: removeGroupNameAliases
keywords: api
sidebar: api_sidebar
permalink: removeGroupNameAliases.html
folder: api
toc: false
---

このコマンドはグループのエイリアス名を削除します。



## API パラメータ



| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :----: | :-------: | :-----------: | --------------------------------------- |
|   aliasName    | 文字列 |   true    |    *null*     | グループのエイリアス |



## API Call テンプレート

```
removeGroupNameAlias aliasName=<groupAliasName>
```



### サンプル API Call

```
removeGroupNameAlias aliasName=testGroupAlias
```



### JSONのSuccess Response

```
{
"data":[
    {
    "aliasName":"testGroupAlias",
    "groupName":"testAliasGroupName"
}
],
"description":"Group Alias removed",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data– 各グループ名エイリアスに関する以下の情報を提供します
  - aliasName – `groupname`のエイリアス
  - groupName – オリジナルのグループ名
- description – コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- webconfig.luaの**hasGroupNameAliases**は **TRUE**に設定されている必要があります。


------

## 関連リンク

- [hasGroupNameAliases](userguide_webconfig.html#hasgroupnamealiases)
- [addGroupNameAliases](addGroupNameAliases.html)
- [listGroupNameAliases](listGroupNameAliases.html)
- [flushGroupNameAliases](flushGroupNameAliases.html)