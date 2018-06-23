---
title: isStreamRunning
keywords: api
sidebar: api_sidebar
permalink: isStreamRunning.html
folder: api
toc: false
---

指定したストリームが実行中かどうかを確認します



## API パラメータ



| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|       id        | 整数値 |   true    |    *null*     | 確認したいストリームの**configID** |
| localStreamName | 文字列  |   true    |    *null*     | 確認したいストリーム名         |

## API Call テンプレート
```
isStreamRunning id=<configId>
```

または

```
isStreamRunning localStreamName=<localStreamName>
```



### サンプル API Call

```
isStreamRunning localStreamName=testpullStream
```



### JSONのSuccess Response

**実行中の場合は:**

```
"data":{
	"Running":true
},
"description":"Stream status:",
"status":"SUCCESS"
```

**実行中でない場合:**

```
"data":{
	"Running":false
},
"description":"Stream status:",
"status":"SUCCESS"
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - Running - **true** または **false**でストリームがアクティブかどうかを示します
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- **id** または **localStreamName** のどちらかのパラメータをAPIコールに含めてください


------

## 関連リンク

- [listStreams](listStreams.html)
- [listStreamsIds](listStreamsIds.html)
- [listConfig](listConfig.html)