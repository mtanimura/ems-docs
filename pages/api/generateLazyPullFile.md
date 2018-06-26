---
title: generateLazyPullFile
keywords: api
sidebar: api_sidebar
permalink: generateLazyPullFile.html
folder: api
toc: false
---


ファイルがリクエストされると、プルされるストリームの情報を持ったVODファイルを作成します。



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-------------------: | :-----: | :--------------------------------------: | :-------------------------: | ---------------------------------------- |
|          uri          | 文字列  |                   true                   |           *null*            | 外部ストリームURI。RTMP、RTSP、ユニキャスト／マルチキャストmpegts等 |
|      pathToFile       | 文字列  |                   true                   |           *null*            | ファイルの保存先パス。拡張子“.vod”が付きます |
|       forceTcp        | ブーリアン |                  false                   |          1 *true*           | **true**でかつストリームがRTSPの場合、TCP接続が強制されます。それ以外では転送メカニズムはネゴシエーションされます(UDPまたはTCP) |
|         tcUrl         | 文字列  |                  false                   |    *zero-length string*     | 初回RTMP生成時に設定値がTC URLに使用されます |
|        pageUrl        | 文字列  |                  false                   |    *zero-length string*     | 初回RTMP生成時に設定値が元ウェブページアドレスとして使用されます |
|        swfUrl         | 文字列  |                  false                   |    *zero-length string*     | 初回RTMP生成時に設定値が元swf URLとして使用されます |
|      rangeStart       | 整数値 |                  false                   |             -2              | RTSPおよびRTMP接続での再生開始点(秒) **-2** と **-1**は特別な設定値で、くわしくは [start/lenパラメータ:](http://livedocs.adobe.com/flashmediaserver/3.0/hpdocs/help.html?content=00000185.html])を参照してください |
|       rangeEnd        | 整数値 |                  false                   |             -1              | 再生する長さ(秒)**-1**は特別な設定値で、くわしくは [start/lenパラメータ:](http://livedocs.adobe.com/flashmediaserver/3.0/hpdocs/help.html?content=00000185.html])を参照してください |
|          ttl          | 整数値 |                  false                   | *operating system supplied* | ソケットのIP_TTL (Time to Live)設定 |
|          tos          | 整数値 |                  false                   | *operating system supplied* | ソケットのIP_TOS (Type of Service)設定 |
| rtcpDetectionInterval | 整数値 |                  false                   |             10              | RTSPストリームがRTCPレスであることを宣言するまでサーバーがRTCPパケットを待つ時間(秒) |
|   emulateUserAgent    | 文字列  |                  false                   |     *EvoStream message*     | ユーザーエージェントストリングとして使用される設定値 RTMPの場合のみ有効 |
|        isAudio        | ブーリアン |    trueif uri is RTP, otherwise false    |          1 *true*           | **true**でかつストリームがRTPの場合、プルされたストリームがオーディオソースであることを意味します。それ以外はプルされたストリームはビデオソースを含むとみなされます |
|    audioCodecBytes    | 文字列  | true if uri is RTP and isAudio is true, otherwise false |    *zero-length string*     | オーディオRTPストリームのオーディオcodec設定 `0x`や`h`をのぞく16進数表記です。*例:  audioCodecBytes=1190* |
|       spsBytes        | 文字列  | true if uri is RTP and isAudio is false, otherwise false |    *zero-length string*     | RTPストリームがビデオの場合のビデオSPSバイト。base64でエンコードする必要があります |
|       ppsBytes        | 文字列  | true if uri is RTP and isAudio is false, otherwise false |    *zero-length string*     | RTPストリームがビデオの場合のビデオPPSバイト。base64でエンコードする必要があります |
|         ssmIp         | 文字列  |                  false                   |    *zero-length string*     | 特定のマルチキャストソースのIP。UDPベースプルの場合のみ使用可 |
|       httpProxy       | 文字列  |                  false                   |    *zero-length string*     |  **IP:Port**という２個の値をとります RTSPストリームが**Self** からプルするRTSP HTTP Proxyを指定します。"self"はRTSP over HTTPを意味します |
|    sendRenewStream    | ブーリアン |                  false                   |          0 *false*          | **true**の場合、サーバーは新規クライント接続があるとSET_PARAMETER経由でRenewStreamを送ります。RTSP URIでのみ有効 |
|       keepAlive       | ブーリアン |                  false                   |          0 *false*          | **true**の場合、全てのクライエントが接続を切断してもソースストリームはシャットダウンしません |



## API Call テンプレート

```
generateLazyPullFile uri=<AddressOfStream> pathToFile=<filePathtoSave/fileName.vod>
```



### サンプル API Call

```
generateLazyPullFile uri=rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4 pathToFile=../media/testGenerateLazyPull.vod
```



### JSONのSuccess Response

```
{
"data":{
    "audioCodecBytes":"",
    "emulateUserAgent":"EvoStream Media Server (www.evostream.com) player",
    "forceTcp":true,
    "httpProxy":"",
    "isAudio":true,
    "keepAlive":false,
    "pageUrl":"",
    "pathToFile":"..\/media\/testGenerateLazyPull",
    "ppsBytes":"",
    "rangeEnd":-1,
    "rangeStart":-2,
    "rtcpDetectionInterval":10,
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
        "host":"s2pchzxmtymn2k.cloudfront.net",
        "ip":"54.239.131.224",
        "originalUri":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
        "parameters":{
        		},
        "password":"",
        "port":1935,
        "portSpecified":false,
        "scheme":"rtmp",
        "userName":""
        }
},
"description":"Stream parameters written to ..\/media\/testGenerateLazyPull.vod",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - audioCodecBytes - RTPストリームがオーディオの場合のオーディオcodec。`0x`や`h`をのぞく16進数表記
  - emulateUserAgent – EMSが他のサーバーと自身を区別するために使用する文字列。EMSが自身をFlash Media Serverと指定する等に使用可能です
  - forceTcp – TCPを強制するかどうか
  - httpProxy – IP:Portの組み合わせまたはself
  - isAudio – プルしたストリームがオーディオソースであるかを示します
  - keepAlive – trueの場合、再生が停止してもcofingにストリームを保持します。
  - pageUrl – リクエスト元ページへのリンク
  - pathToFile – ストリームのローカル名
  - ppsBytes – RTPストリームがビデオの場合そのビデオPPSバイト
  - rangeEnd – 再生の長さ(秒)
  - rangeStart – 再生の開始点。RTSPおよびRTMP接続でのみ有効
  - rtcpDetectionInterval – RTSPで使用され、RTSP/RTPストリームに対しRTCP接続があるかどうかをEMSが待つ時間
  - sendRenewStream – 新規クライントが接続した際サーバーがRenewStreamを送信するかを示します
  - spsBytes – RTPストリームがビデオの場合のビデオSPSバイト
  - ssmIp – ソース特定マルチキャストからのソースIP
  - swfUrl – ストリームを生成しているFlashクライエントの場所
  - tcUrl – RTMPパラメータ（実質的にURIのコピーである)
  - tos – Type of Service ネットワークフラグ
  - ttl – Time To Live ネットワークフラグ
  - uri – key/value ペアでソースストリームURを示します
    - document – ソースストリームのドキュメント名
    - documentPath – ソースストリームのドキュメントパス
    - documentWithFullParameters – ソースストリームのパラメータ付きドキュメント名
    - fullDocumentPath - destinationストリームのドキュメントパス
    - fullDocumentPathWithParameters - destinationストリームのパラメータ付きドキュメントパス
    - fullParameters – ソースストリームURIのパラメータ
    - fullUri – ソースストリームのフルURI
    - fullUriWithAuth – ソースストリームの認証付きフルURI
    - host – ソースストリームホスト名
    - ip – ソースストリームホストのIPアドレス
    - originalUri – ソースストリームが生成されるURI
    - parameters – ソースストリームパラメータ
    - password – ソースストリーム認証パスワード
    - port – ソースストリームポート
    - portSpecified – ソースストリーム用のポートが指定されていればTrue
    - scheme – ソースストリームに使用するプロトコル
    - userName – ソースストリームの認証ユーザ名

- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------
