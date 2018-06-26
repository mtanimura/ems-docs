---
title: pushStream
keywords: api
sidebar: api_sidebar
permalink: pushStream.html
folder: api
toc: false
---



外向けにローカルストリームをプッシュします。プッシュするストリームはRTMP, RTSP,MPEG-TSユニキャスト／マルチキャストプロトコルのみ使用可です。



## API パラメータ

|    パラメータ名    |  タイプ   |                必須かどうか                 |        デフォルト値        | 説明                              |
| :--------------------: | :-----: | :-------: | :-------------------------: | ---------------------------------------- |
|          uri           | 文字列 |   true    |           *null*            | 外部ストリームURI。RTMP,RTSP,ユニキャスト／マルチキャストmpegts等 |
|       keepAlive        | ブーリアン |   false   |          1 *true*           |  `keepAlive` が **true**の場合、接続が切断した際、サーバーはストリームソースとの接続を再構築しようと試行します。再接続は毎秒試行されます |
|    localStreamName     | 文字列 |   true    |           *null*            | プッシュされるストリーム名 |
|    targetStreamName    | 文字列 |   false   |           *null*            | ターゲットストリーム名。設定が無い場合、local stream nameと同じものが使用されます |
|    targetStreamType    | 文字列 |   false   |            live             |  **live**, **record**, **append**のいずれかを設定可。RTMPでのみ有効 |
|         tcUrl          | 文字列 |   false   |    *zero-length string*     | 設定されている場合、初回RTMP接続でTC URLの設定に使用されます |
|        pageUrl         | 文字列 |   false   |    *zero-length string*     | 設定されている場合、初回RTMP接続で設定値が起点webページアドレスに設定されます |
|         swfUrl         | 文字列 |   false   |    *zero-length string*     | 設定されている場合、初回RTMP接続で設定値が起点swf URLに設定されます |
|          ttl           | 整数値 |   false   | *operating system supplied* | IP_TTL (Time to Live)オプションの設定 |
|          tos           | 整数値 |   false   | *operating system supplied* | IP_TOS (Type of Service)オプションの設定 |
|    emulateUserAgent    | 文字列 |   false   |     *EvoStream message*     | user agent stringとして使用する設定値 RTMPでのみ有効 |
| rtmpAbsoluteTimestamps | ブーリアン |   false   |          0 *false*          | RTMP使用時にタイムスタンプに絶対値を強制します |
|  sendChunkSizeRequest  | ブーリアン |   false   |          1 *true*           | RTMPストリームが“Set Chunk Length”メッセージを送信するかどうかを設定します。AkamaiのRTMP HD ingest pointにプッシュする場合に、Akamaiが接続をドロップしないようにこのパラメータは0に設定される必要があるという意味で重要です |
|      useSourcePts      | ブーリアン |   false   |          0 *false*          | trueの場合、ソースインバウンドRTMP上のタイムスタンプが直接アウトバウンド(プッシュ)RTMPストリームに渡されます。netRTMPソースをアウトバウンドNet RTMPプッシュする場合にのみ有効です。この設定は、config.luaでの同名オプションの設定より優先されます |
|       httpProxy        | 文字列 |   false   |    *zero-length string*     | **IP:Port**とipおよびポートの２つの値を設定 – 設定値はRTSPストリームをプルするRTSP HTTP Proxyを指定。**self**と指定した場合はRTSP over HTTPを意味します |





## API Call テンプレート

```
pushStream uri=<AddressOfStream> localStreamname=<localStreamName> targetStreamName=<targetStreamName>
```



### サンプル API Call

```
pushStream uri=rtmp://192.168.1.200/live localStreamName=testpullStream targetStreamName=testpushStream
```



### JSONのSuccess Response

```
{
"data":{
"configId":2,
"emulateUserAgent":"EvoStream Media Server (www.evostream.com)",
"forceTcp":false,
"httpProxy":"",
"keepAlive":true,
"localStreamName":"testpullStream",
"operationType":2,
"pageUrl":"",
"rtmpAbsoluteTimestamps":false,
"sendChunkSizeRequest":true,
"swfUrl":"",
"targetStreamName":"testpushStream",
"targetStreamType":"live",
"targetUri":{
	"document":"live",
	"documentPath":"\/",
	"documentWithFullParameters":"live",
	"fullDocumentPath":"\/live",
	"fullDocumentPathWithParameters":"\/live",
	"fullParameters":"",
	"fullUri":"rtmp:\/\/192.168.1.200\/live",
	"fullUriWithAuth":"rtmp:\/\/192.168.1.200\/live",
	"host":"192.168.1.200",
	"ip":"192.168.1.200",
	"originalUri":"rtmp:\/\/192.168.1.200\/live",
	"parameters":{
		},
	"password":"",
	"port":1935,
	"portSpecified":false,
	"scheme":"rtmp",
	"userName":""
},
"tcUrl":"",
"tos":256,
"ttl":256,
"useSourcePts":false
},
"description":"Local stream testpullStream enqueued for pushing to rtmp:\/\/192.168.1.200\/live as testpushStream",
"status":"SUCCESS"
}
```



#### JSON Response

pullStreamに対するJSON responseは下記の詳細を含みます:

- data – パースすべきデータ
  - configID – コマンドのconfig id
  - emulateUserAgent – EMSが他のサーバーと自身を区別するために使用する文字列。EMSが自身をFlash Media Serverと指定する等に使用可能です
  - forceTcp – TCPを強制するかどうか、またはUDPを許容するか
  - httpProxy - **IP:Port**の組み合わせまたは**Self**
  - keepAlive – **true**の場合、接続が切断した場合にストリーム再接続を試行する
  - localStreamName – ストリームのローカル名
  - operationType – オペレーションタイプ
  - pageUrl – リクエスト元のページへのリンク（あまり使われません）
  - rtmpAbsoluteTimeStamps – If **true**, forces the timestamps to be absolute when using RTMP
  - sendChunkSizeRequest – Indicates whether theRTMP stream will or will not send a “Set Chunk Length” message
  - swfUrl – ストリームを生成しているFlash Clientの場所（もしあれば）
  - tcUrl – RTMPのパラメーターで実質的にはURIのコピー
  - tos – Service network flagタイプ
  - ttl – Time To Liveネットワークフラグ
  - targeturi – ソースストリームURIが記述されたkey/valueペア
    - document – ソースストリームのdocument名
    - documentPath – ソースストリームのdocumentパス
    - documentWithFullParameters – ソースストリームのパラメータ付きdocument名
    - fullDocumentPath - destinationストリームのdocumentパス
    - fullDocumentPathWithParameters - destinationストリームのパラメータ付きdocumentパス
    - fullParameters – ソースストリームURI用パラメータ
    - fullUri – ソースストリームのフルURI
    - fullUriWithAuth – ソースストリームの認証付きフルURI
    - host – ソースストリームホスト名
    - ip – ソースストリームホストのipアドレス
    - originalUri – ソースストリームが生成されているURI
    - parameters – ソースストリームURI用のパラメータ（もしあれば）
    - password – ソースストリームの認証パスワード(必要な場合)
    - port – ソースストリームが使用するポート
    - portSpecified – ソースストリームのポートが指定されている場合はtrue
    - scheme – ソースストリームが使用するプロトコル
    - userName – ソースストリームを認証する際のユーザ名(必要な場合)
- description– コマンドパース／実行時の結果
- status – コマンドが正常にパース／実行された場合は**SUCCESS**、そうでなければ **FAIL**

------

## 関連リンク

- [Sending Streams](userguide_send.html)
- [Push a Stream](userguide_pushstream.html)