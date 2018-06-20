---
title: pullStream
keywords: api
sidebar: api_sidebar
permalink: pullStream.html
folder: api
toc: false
---


外部ソースからストリームをプルします。ストリームがプルされると、"local stream name"が割り当てられ、これはEMS内でのアクセスに利用できます。



## API パラメータ

|    パラメータ名    |  タイプ   |                必須かどうか                 |        デフォルト値        | 説明                              |
| :-------------------: | :-----: | :--------------------------------------: | :-------------------------: | ---------------------------------------- |
|          uri          | 文字列 |                   true                   |           *null*            | 外部ストリームURI RTMP,RTSP,ユニキャスト／マルチキャストmpegts等 |
|       keepAlive       | ブーリアン |                  false                   |          1 *true*           | `keepAlive` が **true**の場合、接続が切断した際、サーバーはストリームソースとの接続を再構築しようと試行します。再接続は毎秒試行されます |
|    localStreamName    | 文字列 |                  false                   |         *generated*         | 設定があれば名前付けられます。設定がなければ、URIに基づいた名前が割り当てられます |
|       forceTcp        | ブーリアン |                  false                   |          0 *false*          | 設定が **true** でRTSPストリームの場合はTCP接続が強制されます。それ以外はUDPかTCPでネゴシエーションされます |
|         tcUrl         | 文字列 |                  false                   |    *zero-length string*     | 設定されている場合、初回RTMP接続でTC URLの設定に使用されます |
|        pageUrl        | 文字列 |                  false                   |    *zero-length string*     | 設定されている場合、初回RTMP接続で設定値が起点webページアドレスに設定されます |
|        swfUrl         | 文字列 |                  false                   |    *zero-length string*     | 設定されている場合、初回RTMP接続で設定値が起点swf URLに設定されます |
|      rangeStart       | 整数値 |                  false                   |             -2              | RTSPおよびRTMP接続で、再生がスタートする設定値（秒）。**-2** と **-1**は特別な値です。くわしくはAdobe Flash Media Serverを参照してください |
|       rangeEnd        | 整数値 |                  false                   |             -1              | 再生の秒数 **-1** は特別な値です。くわしくはAdobe Flash Media Serverを参照してください |
|          ttl          | 整数値 |                  false                   | *operating system supplied* | IP_TTL (Time to Live)オプションの設定 |
|          tos          | 整数値 |                  false                   | *operating system supplied* | IP_TOS (Type of Service)オプションの設定 |
| rtcpDetectionInterval | 整数値 |                  false                   |             10              | RTCP-less streamとして宣言するまでにサーバーがRTCPパケットを待つ秒数 |
|   emulateUserAgent    | 文字列 |                  false                   |     *EvoStream message*     | user agent stringとして使用する設定値 RTMPでのみ有効 |
|        isAudio        | ブーリアン |    uriがRTPの場合はtrue その他はfalse    |          1 *true*           | **true**の場合でかつストリームがRTPの場合、 プルされるストリームがオーディオソースであることを示します。それ以外の場合はプルするストリームはビデオソースとみなします |
|    audioCodecBytes    | 文字列 | uriがRTPの場合はtrueかつisAudioもtrue その他はfalse |    *zero-length string*     | RTPストリームがaudioの場合にaudio codecを設定します `0x`または`h`を省いた16進数フォーマット*例:  audioCodecBytes=1190* |
|       spsBytes        | 文字列 | uriがRTPの場合はtrueかつisAudioはfalse その他はfalse |    *zero-length string*     | ビデオストリームの場合のRTPストリームのSPS byte base64でエンコードする必要があります |
|       ppsBytes        | 文字列 | uriがRTPの場合はtrueかつisAudioはfalse その他はfalse |    *zero-length string*     | ビデオストリームの場合のRTPストリームのPPS byte base64でエンコードする必要があります |
|         ssmIp         | 文字列 |                  false                   |    *zero-length string*     | source-specific-multicastのソースip。UDPベースのプルの場合のみ使用可能 |
|       httpProxy       | 文字列 |                  false                   |    *zero-length string*     | **IP:Port**とipおよびポートの２つの値を設定 – 設定値はRTSPストリームをプルするRTSP HTTP Proxyを指定。**self**と指定した場合はRTSP over HTTPを意味します |
|    sendRenewStream    | ブーリアン |                  false                   |          0 *false*          | **true**の場合、新規クライエントが接続した際、サーバーはSET_PARAMETERでRenewStreamを送信します。RTSP URIでのみ有効 |

## API Call テンプレート

```
pullStream uri=<AddressOfStream> localStreamname=<localStreamName>
```



### サンプル API Call

```
pullstream uri=rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4 localstreamname=testpullStream
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
"swfUrl":"",
"tcUrl":"",
"tos":256,
"ttl":256,
"uri":{
"document":"mp4:sintel.mp4",
"documentPath":"\/cfx\/st\/",
"documentWithFullParameters":"mp4:sintel.mp4",
"fullDocumentPath":"\/cfx\/st\/mp4:sintel.mp4",
"fullDocumentPathWithParameters":"\/cfx\/st\/mp4:sintel.mp4",
"fullParameters":"",
"fullUri":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
"fullUriWithAuth":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
"generatedPort":0,
"host":"s2pchzxmtymn2k.cloudfront.net",
"ip":"204.246.165.200",
"originalUri":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
"parameters":{
},
"password":"",
"port":1935,
"portSpecified":false,
"scheme":"rtmp",
"userName":""
},
"videoSourceIndex":"high"
},
"description":"Stream rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4 enqueued for pulling",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは下記の詳細を含みます:

- data – パースするデータ
  - audioCodecBytes - RTPストリームがaudioの場合、RTPストリームでのオーディオ
  - configID – コマンドのconfig id
  - emulateUserAgent – EMSが自身を同定するために使用する文字列。EMSが自身を同定するのにたとえばFlash Media Serverなどと変更することが可能
  - forceTcp – TCPを強制するかどうか、またはUDPを許容するか
  - httpProxy - **IP:Port**の組み合わせまたは**Self**
  - isAudio - プルされているストリームがaudioソースであることを示す
  - keepAlive – **true**の場合、接続が切断した場合にストリーム再接続を試行する
  - localStreamName – ストリームのローカル名
  - operationType – オペレーションタイプ、内部使用
  - pageUrl – リクエスト元のページへのリンク（あまり使われません）
  - ppsBytes - ビデオの場合のRTPストリームのvideo PPS bytes
  - rangeEnd - 再生の長さ（秒）
  - rangeStart - 再生のスタート位置(秒)
  - rtcpDetectionInterval – RTSPで使用。RTSP/RTPストリームでRTCP接続が使用可能か判定する待ち時間(ビデオ・オーディオの同期に使用)
  - sendRenewStream – **true**の場合、新規クライエント接続があった際サーバーは**SET_PARAMETER**経由で`sendRenewStream`を行う
  - spsBytes - ビデオの場合、RTPストリームのビデオSPSバイト
  - ssmIp - source-specific-multicastのソースIP
  - swfUrl – ストリームを生成しているFlash Clientの場所（もしあれば）
  - tcUrl – RTMPのパラメーターで実質的にはURIのコピー
  - tos – Service network flagタイプ
  - ttl – Time To Liveネットワークフラグ
  - uri – ソースストリームURIが記述されたkey/valueペア
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
  - videoSourceIndex - ビデオ解像度


- description– コマンドパース／実行時の結果


- status – コマンドが正常にパース／実行された場合は**SUCCESS**、そうでなければ **FAIL**

------

## 関連リンク

- [Adding Streams](userguide_add.html)
- [Pull a Stream](userguide_pullstream.html)
