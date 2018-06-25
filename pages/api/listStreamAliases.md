---
title: listStreamAliases
keywords: api
sidebar: api_sidebar
permalink: listStreamAliases.html
folder: api
toc: false
---

エイリアスのリストを返します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
listStreamAliases
```



### JSONのSuccess Response

```
{
"data":[
    {
    "aliasName":"testAlias",
    "creationTime":1448267205,
    "expirePeriod":0,
    "localStreamName":"testpullStream",
    "oneShot":false,
    "permanent":false
}
],
"description":"Currently available aliases",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – `aliasName`と`localStreamName`の組み合わせのアレイ
  - aliasName – `localStreamName`のエイリアス
  - creationTime – エイリアスが作成された時間
  - expirePeriod - エイリアスの有効期限
  - localStreamName – オリジナルのストリーム名
  - oneShot - エイリアスが一回のみの使用かどうかを決定
  - permanent - エイリアスがEMSが再起動されるまで永続的にに使用できるかを決定
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- config.luaの**hasStreamAliases**は**TRUE**である必要があります。


------

## 関連リンク

- [hasStreamAliases](userguide_configlua.html#hasstreamaliases)
- [addStreamAlias](addStreamAlias.html)
- [removeStreamAlias](removeStreamAlias.html)
- [flushStreamAliases](flushStreamAliases.html)