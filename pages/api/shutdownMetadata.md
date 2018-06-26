---
title: shutdownMetadata
keywords: api
sidebar: api_sidebar
permalink: shutdownMetadata.html
folder: api
toc: false
---

メタデータpseudoストリームを停止します。このコマンドは与えられた`localStreamName`に発行されたすべての複数のプルストリームをシャットダウンします。



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-------------: | :----: | :-------: | :-----------: | ---------------------------------------- |
| localStreamName | 文字列 |   true    |    *null*     | 入力ストリーム名に関連するメタデータ |



## API Call テンプレート

```
shutdownMetadata localStreamName=<localStreamName>
```



### サンプル API Call

```
shutdownMetadata localStreamName=testpullStream
```



### JSONのSuccess Response

```
{
"data":{
    "localStreamName":"testpullStream",
    "streamName":"testpullStream",
    "type":"vmf"
},
"description":"Shutdown Metadata Push Stream",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - localStreamName – 関連メタデータが送られるストリーム名
  - streamName – 関連メタデータが送られるストリーム名
  - type – ストリームタイプ


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [pushMetadata](pushMetadata.html)
- [getMetadata](getMetadata.html)