---
title: uploadMedia
keywords: api
sidebar: api_sidebar
permalink: uploadMedia.html
folder: api
toc: false
---

HTTP POSTバイナリアップロードを受信するacceptorを作成します。特定ポート上でacceptorは開かれ、アップロードメディアファイルは特定のディレクトリに保存されます。acceptorはクライエントからメディアファイルをペイロードとするHTTP POSTを待ちます。メディアファイルはサーバーの特定の場所に書き込まれます。



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|      port      | integer |   true    |    *null*     | バインドされるポート |
|  targetFolder  | string  |   true    |    *null*     | バイナリアップロードが配置されるフォルダ |



## API Call テンプレート

```
uploadMedia port=<portNumber> targetFolder=<targetFolder>
```



### サンプル API Call

```
uploadMedia port=3333 targetFolder=../media
```



### JSONのSuccess Response

```
{
"data":{
    "ip":"0.0.0.0",
    "port":3333,
    "targetFolder":"..\/media"
},
"description":"Media upload acceptor configuration.",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - ip – EMSを参照するIP 通常 0.0.0.0
  - port – acceptorがHTTP POSTを受け付けるポート
  - targetFolder – メディアファイルが保存されるフォルダ


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- メディアを送信するクライエントは下記に従う必要があります
  - HTTP POSTを使用してデータを送信
  - POSTリクエストは http/1.1 フォーマット
  - StreamNameがPOSTの中で指定されていること、これはメディアファイル(mp4) 名に使用されます(例 *POST /mystreamname HTTP/1.1\r\n*)
  - Content-typeは *video/mp4* または *application/octet-stream*に指定
  - Content-length が必要。VOD MP4のアップロードに使用されるため、ファイルサイズは予めわかっていると想定


