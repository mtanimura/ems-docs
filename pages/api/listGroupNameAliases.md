---
title: listGroupNameAliases
keywords: api
sidebar: api_sidebar
permalink: listGroupNameAliases.html
folder: api
toc: false
---

エイリアスの全リストを返します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
listGroupAliases
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
"description":"Currently available group name aliases",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data– 各グループ名エイリアスについて次の情報が提供されます
  - aliasName – `groupname`のエイリアス
  - groupName – オリジナルのグループ名
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- webconfig.luaの**hasGroupNameAliases**は**TRUE**である必要があります


------

## 関連リンク

- [hasGroupNameAliases](userguide_webconfig.html#hasgroupnamealiases)
- [addGroupNameAliases](addGroupNameAliases.html)
- [getGroupNameByAlias](getGroupNameByAlias.html)
- [removeGroupNameAliases](removeGroupNameAliases.html)
- [flushGroupNameAliases](flushGroupNameAliases.html)