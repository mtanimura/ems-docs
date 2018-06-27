---
title: shutdownStream
keywords: api
sidebar: api_sidebar
permalink: shutdownStream.html
folder: api
toc: false
---

特定のストリームを終了します。`permanently=1`が使用される場合、このコマンドは`removeConfig`と同義です



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-------------: | :-----: | :-------: | :------------------: | ---------------------------------------- |
|       id        | 整数値 |   true    |         null         | 終了するストリームのユニークid。ストリームIDは`listStreams`コマンドで参照できます。このパラメータは必須ではありませんが、このパラメータまたは`localStreamName`のどちらかがストリームの特定に必要です
| localStreamName | 文字列  |   true    | *zero length string* | 終了したいインバウンドストリーム名、入力ストリームに依存するアウトバウンドストリームも一緒に終了します。このパラメータは必須ではありませんが、このパラメータまたはidがストリーム特定に必要です |
|   permanently   | ブーリアン |   false   |       1 *true*       | **true**の場合、一致するpush/pull設定も削除されます。したがってサーバーが再起動した際ストリーム再接続は行われません。 |

## API Call テンプレート

```
shutdownstream id=<configId>
```

または

```
shutdownstream localStreamName=<localStreamName>
```



### サンプル API Call

```
shutdownstream localStreamName=testpullStream permanently=1
```



### JSONのSuccess Response

```
{
"data":{
    "protocolStackInfo":{
    "carrier":{
    "farIP":"54.239.131.57",
    "farPort":1935,
    "id":601,
    "nearIP":"192.168.2.35",
    "nearPort":2326,
    "rx":3077367,
    "tx":3653,
    "type":"IOHT_TCP_CARRIER"
    },
    "stack":[
    {
    "applicationId":0,
    "creationTimestamp":1448008702269.8640,
    "id":794,
    "isEnqueueForDelete":false,
    "queryTimestamp":1448008724139.1150,
    "type":"TCP"
    },
    {
    "applicationId":1,
    "creationTimestamp":1448008702269.8640,
    "id":795,
    "isEnqueueForDelete":false,
    "queryTimestamp":1448008724139.1150,
    "rxInvokes":31,
    "serverAgent":"FMS\/3,5,7,7009",
    "streams":[
    {
    "appName":"evostreamms",
    "audio":{
        "bytesCount":348883,
        "codec":"AAAC",
        "codecNumeric":4702111241970122752,
        "droppedBytesCo unt":0,
        "droppedPacketsCount":0,
        "packetsCount":1068
        },
    "bandwidth":0,
    "connectionTyp e":1,
    "creationTimestamp":1448008702871.8989,
    "farIp":"54.239.131.57",
    "farPort":1935,
    "ip":"192.168.2.35",
    "name":"testpullstream",
    "nearIp":"192.168.2.35",
    "nearPort ":2326,
    "outStreamsUniqueIds":[91],
    "pageUrl":"",
    "port":2326,
    "processId":12848,
    "processType":"origin",
    "pullSettings":{
    "_callback":null,
    "audioCodecBytes":"",
    "configId":1,
    "emulateUserAgent":"EvoStream Media Server (www.evostream.com) player",
    "forceTcp":false,
    "httpProxy":"",
    "isAudio":true,
    "keepAlive":true,
    "localStreamName":"testpullstream",
    "operationType":1,
    "pageUrl":"",
    "ppsBytes":"",
    "rangeEnd":-1,
    "ran geStart":-2,
    "rtcpDetectionInterval":10,
    "sendRenewStream":false,
    "spsBytes":"",
    "ss mIp":"",
    "swfUrl":"",
    "tcUrl":"",
    "tos":256,
    "ttl":256,
    "uri":"rtmp:\/\/s2pchzxmtymn2 k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4"
    },
    "queryTimestamp":1448008724139.1150,
    "serverAgent":"FMS\/3,5,7,7009",
    "swfUrl":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net \/cfx\/st\/mp4:sintel.mp4",
    "tcUrl":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
    "type":"INR",
    "typeNumeric":5282249572905648128,
    "uniqueId":95,
    "upTime":21267.2161,
    "video":{
        "bytesCount":2698244,
        "codec":"VH264",
        "codecNumeric":6217274493967007744,
        "droppedBytesCount":0,
        "droppedPacketsCount":0,
        "height":306,
        "level":30,
        "packetsCount":596,
        "profile":66,
        "width":720
        }
    }
    ],
    "txInvokes":7,
    "type":"OR"
    }
    ]
    },
    "streamInfo":{
        --Same with streams group
        }
    }
},
"description":"Stream closed",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - protocolStackInfo – ストリームに使用されるプロトコル・スタックのキー／値ペアを含みます
     - carrier - 接続に関する詳細情報
      - farIp - far側のIPアドレス
      - farPort - far側の使用ポート
      - nearIp - ローカルコンピューターで使用されるIPアドレス
      - nearPort - ローカルコンピューターで使用されるポート
      - rx – この接続で受信したバイト総数
      - tx – この接続で転送されたバイト総数
      - type – 接続タイプ(TCP, UDP)
    - stack[1] – farthest protocol primitiveについて
      - applicationID – 接続を使用する内部アプリケーションID
      - creationTimestamp – アプリケーションが接続の使用を開始したUNIX時間
      - id – stack relationのユニークID
      - isEnqueueForDelete – 削除に用いられる内部フラグ
      - queryTimestamp – データがクエリーされたUNIX時間
      - type – アプリケーションが接続をどのように使用するかについての記述子
    - stack[2] – next protocol primitiveについて
      - applicationID – 接続を使用する内部アプリケーションID
      - creationTimestamp – アプリケーションが接続の使用を開始したUNIX時間
      - id – stack relationのユニークID
      - isEnqueueForDelete – 削除スケジュール
      - queryTimestamp – データがクエリーされたUNIX時間
      - rxInvokes – RTMP関数がinvokeされた回数
      - streams[1]
        - audio – ストリームのオーディオ部分の統計情報
          - bytesCount - 受信したオーディオデータ総量
          - droppedBytesCount - ロストしたビデオバイト数
          - droppedPacketsCount – ロストオーディオパケット数
          - packetsCount – 受信オーディオパケット総数
        - bandwidth – ストリームの現在の使用帯域
        - canDropFrames – *アウトストリームのみ*  クライエントによりセットされるフラグでフレーム／パケット落ちを許可
        - creationTimestamp – ストリーム生成時点のUNIXタイムスタンプ。UNIXタイムはUNIXエポック(1970年1月1日)からの秒数です
        - inStreamUniqueID – *プッシュストリーム*のソースストリームid
        - name – ストリームの`localStreamName`
        - queryTimestamp – データがクエリーされたUNIX時間
        - type – ストリームタイプ。くわしくは`getStreamInfo`を参照
        - uniqueId – ストリームのuniqueID(整数値)
        - upTime – ストリームがaliveかつ実行中の期間(秒数)
        - video
          - bytesCount - 受信ビデオデータ総量
          - droppedBytesCount – ロストしたビデオバイト数
          - droppedPacketsCount – ロストしたビデオパケット数
          - packetsCount – 受信したビデオパケット数
      - streams[2]
        - bandwidth – ストリームの現在の使用帯域
        - creationTimestamp – ストリーム生成時点のUNIXタイムスタンプ
        - name – ストリームの`localStreamName`
        - outStreamsUniqueIDs – *プルストリームの際* 入力ストリームに関連する出力ストリームIDのアレイ
        - queryTimestamp – データがクエリーされたUNIX時間
        - type – ストリームタイプ。くわしくは`getStreamInfo`を参照
        - uniqueId – ストリームのuniqueID(整数値)
        - upTime – ストリームがaliveかつ実行中の期間(秒数)
      - txInvokes – 送られたRTMP関数がinvokeされた回数
      - type – アプリケーションが接続をどのように使用するかについての記述子
  - streamInfo
    - bandwidth – ストリームの現在の使用帯域
    - creationTimestamp – ストリーム生成時点のUNIXタイムスタンプ
    - name – ストリームの`localStreamName`
    - outStreamsUniqueIDs – *プルストリームの際* 入力ストリームに関連する出力ストリームIDのアレイ
    - queryTimestamp – データがクエリーされたUNIX時間
    - type – ストリームタイプ。くわしくは`getStreamInfo`を参照
    - uniqueId – ストリームのuniqueID(整数値)
    - upTime – ストリームがaliveかつ実行中の期間(秒数)


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- `listStreams` コマンドで参照できるストリームIDは`listConfig`コマンドで参照できるconfig IDとは違うものです。`shutdownStream` コマンドはストリームIDを使用します。


------

## 関連リンク

- [removeConfig](removeConfig.html)