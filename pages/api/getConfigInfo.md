a---
title: getConfigInfo
keywords: api
sidebar: api_sidebar
permalink: getConfigInfo.html
folder: api
toc: false
---



configIdによるストリーム情報を返す



## API パラメータ


| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|       id       | 整数値 |   true    |    *null*     | `configId`による設定情報取得のid |

## API Call テンプレート

```
getConfigInfo id=<configId>
```



### サンプル API Call

```
getConfigInfo id=1
```



### JSONのSuccess Response

```
{
"data":{
"audioCodecBytes":"",
"configId":1,
"emulateUserAgent":"EvoStream Media Server (www.evostream.com) player",
"forceTcp":false,
"httpProxy":"",
"httpStreamType":"ts",
"isAudio":true,
"keepAlive":true,
"localStreamName":"testpullStream",
"operationType":1,
"pageUrl":"",
"ppsBytes":"",
"rangeEnd":-1,
"rangeStart":-2,
"rtcpDetectionInterval":10,
"saveToConfig":true,
"sendDummyPayload":false,
"sendRenewStream":false,
"spsBytes":"",
"ssmIp":"",
"status":{
"current":{
"code":0,
"description":"Streaming",
"timestamp":1508500111,
"uniqueStreamId":1
},
"previous":{
"code":3,
"description":"Connected",
"timestamp":1508500111,
"uniqueStreamId":0
}
},
"swfUrl":"",
"tcUrl":"",
"tos":256,
"ttl":256,
"uri":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
"videoSourceIndex":"high"
},
"description":"Configuration Info",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – 設定に関する情報
  - 他のフィールド内容はストリームタイプによって異なります


- description – コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- レスポンスは設定によってことなります


------

## 関連リンク

- [listConfig](listConfig.html)
- [removeConfig](removeConfig.html)