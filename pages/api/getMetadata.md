---
title: getMetadata
keywords: api
sidebar: api_sidebar
permalink: getMetadata.html
folder: api
toc: false
---

Metadata Managerによりキャッシュされている最近受信した文字列を返します。ステートレスコールですので複数のクライエントがそれぞれメタデータをポーリングしても性能にインパクトは与えません。新規文字列が届いてなければ、同じ文字列が複数回返ってくるでしょう。


## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
| localStreamName | 文字列  |   true    |    *null*     | 関連メタデータが返される入力ストリーム名。デフォルトは最近のストリーム |
|    streamId     | 整数値 |   false   |       0       | 関連メタデータが返されるストリーム。デフォルトは最近のストリーム |
|     noWrap      | ブーリアン |   false   |   0 *false*   | **true**の場合、返り値文字列はCLI JSONラッピングされません |



## API Call テンプレート

```
getMetadata localStreamName=<localStreamName>
```



### サンプル API Call

```
getMetadata localStreamName=testpullStream noWrap=0
```

```
getMetadata localStreamName=testpullStream noWrap=1
```

### JSONのSuccess Response

```
{
"data":"{\"EMS\":{\"type\":\"json\",\"timestamp\":46125},\"data\":{\"lat\":\"32.809668\",\"lon\":\"-117.255317\",\"alt\":\"44.7\",\"speed\":\"20\",\"dir\":\"300\"}}",
"description":"Metadata",
"status":"SUCCESS"
}
```

```
{
"EMS":{
    "type":"json",
    "timestamp":12042
	},
"data":{
    "lat":"32.809668",
    "lon":"-117.255317",
    "alt":"44.7",
    "speed":"50",
    "dir":"300"
	}
}
```

#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - type - レスポンスタイプ
  - timestamp -  メタデータが生成されたタイムスタンプ
  - lat - 緯度
  - lon - 経度
  - alt -標高
  - speed - スピード
  - dir - 方位


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Related Links

- [pushMetadata](pushMetadata.html)
- [shutdownMetadata](shutdownMetadata.html)