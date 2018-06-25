---
title: flushGroupNameAliases
keywords: api
sidebar: api_sidebar
permalink: flushGroupNameAliases.html
folder: api
toc: false
---



すべてのグルーム名エイリアスを無効化します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
flushGroupNameAliases
```



### JSONのSuccess Response

```
{
"data":null,
"description":"All group name aliases are flushed",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータはありません
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## Notes

-  webconfig.luaの**hasGroupNameAliases**は**TRUE**である必要があります

------

## 関連リンク

- [hasGroupNameAliases](userguide_webconfig.html#hasgroupnamealiases)
- [addGroupNameAliases](addGroupNameAliases.html)
- [getGroupNameByAlias](getGroupNameByAlias.html)
- [listGroupNameAliases](listGroupNameAliases.html)
- [removeGroupNameAliases](removeGroupNameAliases.html)

