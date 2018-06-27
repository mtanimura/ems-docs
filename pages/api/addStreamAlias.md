---
title: addStreamAlias
keywords: api
sidebar: api_sidebar
permalink: addStreamAlias.html
folder: api
toc: false
---


内部ストリームの二次的な名前を生成します。エイリアスが作られるとlocalstreamnameはストリームの再生に使用できなくなります。エイリアスは通常一度つかわれると(クライエントからリクエストがあると)以降は無効となります。エイリアスはソースストリームの保護や隠蔽に使用されます。





## API パラメータ


| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-------------: | :-----: | :-------: | :--------------: | ---------------------------------------- |
| localStreamName | 文字列  |   true    |      *null*      | ストリーム名                |
|    aliasName    | 文字列  |   true    |      *null*      | `localStreamName`のエイリアス |
|  expirePeriod   | 整数値 |   false   | -600 *(10 mins)* | エイリアスの有効期限。負の値は１回のみ使用で絶対値数(秒)以下の有効期限となります。0は無期限。正数は複数回使用可で設定値(秒)で期限切れとなります。デフォルトは-600(1回のみ、10分)です |



## API Call テンプレート

```
addStreamAlias localStreamName=<localStreamName> aliasName=<aliasName>
```



### サンプル API Call

```
addStreamAlias localStreamName=testpullStream aliasName=testStreamAlias expirePeriod=0
```

`localStreamName`が“**testpullStream**”ストリームは“**testStreamAlias**”というエイリアスを持ちます



### JSONのSuccess Response

```
{
"data":{
    "aliasName":"testAlias",
    "expirePeriod":0,
    "localStreamName":"testpullStream"
},
"description":"Alias applied",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - aliasName – `localStreamName`のエイリアス
  - expirePeriod – エイリアスの有効期限
  - localStreamName – 元のストリーム名
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**




## VODでのエイリアス

VODストリームについてもエイリアスを設定できます:

```
addStreamAlias localStreamName=mp4:myfile.mp4 aliasName=myVODalias expirePeriod=0
```

“**myfile.mp4**”というファイル名のメディアファイルは“**myVODalias**”というエイリアスを持ちます

------

## Notes

- config.lua内の**hasStreamAliases** は **TRUE**にする必要があります。
- VODをソースストリームとする場合、VODエイリアスを先に設定する必要があります、そうでないとEMSはファイルを見つけられません。


------

## 関連リンク

- [hasStreamAliases](userguide_configlua.html#hasstreamaliases)
- [listStreamAliases](listStreamAliases.html)
- [removeStreamAlias](removeStreamAlias.html)
- [flushStreamAliases](flushStreamAliases.html)

