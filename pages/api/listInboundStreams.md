---
title: listInboundStreams
keywords: api
sidebar: api_sidebar
permalink: listInboundStreams.html
folder: api
toc: false
---


全てのインバウンド`localStreamNames`の詳細なリストを返します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
listInboundStreams
```



### JSONのSuccess Response

```
{
          "data": {
                    "data": [
                              {
                                        "appName": "evostreamms",
                                        "audio": {
                                                  "aveAudioBitRate": 102226.8169,
                                                  "bytesCount": 940870,
                                                  "codec": "AAAC",
                                                  "codecNumeric": 4702111241970123000,
                                                  "currAudioBitRate": 96889.6,
                                                  "droppedBytesCount": 0,
                                                  "droppedPacketsCount": 0,
                                                  "packetsCount": 3523
                                        },
                                        "bandwidth": 0,
                                        "connectionType": 1,
                                        "creationTimestamp": 1508320715972.891,
                                        "edgePid": 0,
                                        "farIp": "127.0.0.1",
                                        "farPort": 1935,
                                        "ip": "127.0.0.1",
                                        "name": "bunnyqwe",
                                        "nearIp": "127.0.0.1",
                                        "nearPort": 6448,
                                        "outStreamsUniqueIds": null,
                                        "pageUrl": "",
                                        "port": 6448,
                                        "processId": 612,
                                        "processType": "origin",
                                        "pullSettings": {
                                                  "_callback": null,
                                                  "audioCodecBytes": "",
                                                  "configId": 1,
                                                  "emulateUserAgent": "EvoStream Media Server (www.evostream.com) player",
                                                  "forceTcp": false,
                                                  "httpProxy": "",
                                                  "httpStreamType": "ts",
                                                  "isAudio": true,
                                                  "keepAlive": true,
                                                  "localStreamName": "bunnyqwe",
                                                  "operationType": 1,
                                                  "pageUrl": "",
                                                  "ppsBytes": "",
                                                  "rangeEnd": -1,
                                                  "rangeStart": -2,
                                                  "rtcpDetectionInterval": 10,
                                                  "saveToConfig": true,
                                                  "sendDummyPayload": false,
                                                  "sendRenewStream": false,
                                                  "spsBytes": "",
                                                  "ssmIp": "",
                                                  "swfUrl": "",
                                                  "tcUrl": "",
                                                  "tos": 256,
                                                  "ttl": 256,
                                                  "uri": "rtmp://localhost/vod/bunny.mp4",
                                                  "videoSourceIndex": "high"
                                        },
                                        "queryTimestamp": 1508320789466.095,
                                        "serverAgent": "FMS/3,0,1,123",
                                        "swfUrl": "rtmp://localhost/vod/bunny.mp4",
                                        "tcUrl": "rtmp://localhost/vod/bunny.mp4",
                                        "type": "INR",
                                        "typeNumeric": 5282249572905648000,
                                        "uniqueId": 56,
                                        "upTime": 73493.2039,
                                        "video": {
                                                  "aveFrameRate": 24.3944,
                                                  "aveKeyFramesPerSec": 0.3239,
                                                  "aveVideoBitRate": 395857.2394,
                                                  "bytesCount": 3605399,
                                                  "codec": "VH264",
                                                  "codecNumeric": 6217274493967008000,
                                                  "currFrameRate": 24,
                                                  "currKeyFramesPerSec": 0.6,
                                                  "currVideoBitRate": 259859.2,
                                                  "droppedBytesCount": 0,
                                                  "droppedPacketsCount": 0,
                                                  "height": 240,
                                                  "level": 30,
                                                  "packetsCount": 1806,
                                                  "profile": 66,
                                                  "width": 424
                                        }
                              },
                              {
                                        "appName": "evostreamms",
                                        "audio": {
                                                  "aveAudioBitRate": 0,
                                                  "bytesCount": 0,
                                                  "codec": "AAAC",
                                                  "codecNumeric": 4702111241970123000,
                                                  "currAudioBitRate": 0,
                                                  "droppedBytesCount": 0,
                                                  "droppedPacketsCount": 0,
                                                  "packetsCount": 0
                                        },
                                        "bandwidth": 512,
                                        "connectionType": 0,
                                        "creationTimestamp": 1508320715979.892,
                                        "edgePid": 0,
                                        "farIp": "127.0.0.1",
                                        "farPort": 6448,
                                        "ip": "127.0.0.1",
                                        "name": "C:\\EvoStream_2.0\\media\\bunny.mp4",
                                        "nearIp": "127.0.0.1",
                                        "nearPort": 1935,
                                        "outStreamsUniqueIds": [
                                                  57
                                        ],
                                        "port": 1935,
                                        "processId": 612,
                                        "processType": "origin",
                                        "queryTimestamp": 1508320789466.095,
                                        "type": "IFR",
                                        "typeNumeric": 5279997773091963000,
                                        "uniqueId": 58,
                                        "upTime": 73486.2029,
                                        "userAgent": "EvoStream Media Server (www.evostream.com) player",
                                        "video": {
                                                  "aveFrameRate": 0,
                                                  "aveKeyFramesPerSec": 0,
                                                  "aveVideoBitRate": 0,
                                                  "bytesCount": 0,
                                                  "codec": "VH264",
                                                  "codecNumeric": 6217274493967008000,
                                                  "currFrameRate": 0,
                                                  "currKeyFramesPerSec": 0,
                                                  "currVideoBitRate": 0,
                                                  "droppedBytesCount": 0,
                                                  "droppedPacketsCount": 0,
                                                  "height": 240,
                                                  "l,evel": 30,
                                                  "packetsCount": 0,
                                                  "profile": 66,
                                                  "width": 424
                                        }
                              },
                              {
                                        "appName": "evostreamms",
                                        "audio": {
                                                  "aveAudioBitRate": 124868.9032,
                                                  "bytesCount": 549716,
                                                  "codec": "AAAC",
                                                  "codecNumeric": 4702111241970123000,
                                                  "currAudioBitRate": 117090.6667,
                                                  "droppedBytesCount": 0,
                                                  "droppedPacketsCount": 0,
                                                  "packetsCount": 1686
                                        },
                                        "bandwidth": 0,
                                        "connectionType": 1,
                                        "creationTimestamp": 1508320754242.08,
                                        "edgePid": 0,
                                        "farIp": "204.246.165.52",
                                        "farPort": 1935,
                                        "ip": "192.168.2.193",
                                        "name": "testpullStream",
                                        "nearIp": "192.168.2.193",
                                        "nearPort": 6492,
                                        "outStreamsUniqueIds": null,
                                        "pageUrl": "",
                                        "port": 6492,
                                        "processId": 612,
                                        "processType": "origin",
                                        "pullSettings": {
                                                  "_callback": null,
                                                  "audioCodecBytes": "",
                                                  "configId": 3,
                                                  "emulateUserAgent": "EvoStream Media Server (www.evostream.com) player",
                                                  "forceTcp": false,
                                                  "httpProxy": "",
                                                  "httpStreamType": "ts",
                                                  "isAudio": true,
                                                  "keepAlive": true,
                                                  "localStreamName": "testpullStream",
                                                  "operationType": 1,
                                                  "pageUrl": "",
                                                  "ppsBytes": "",
                                                  "rangeEnd": -1,
                                                  "rangeStart": -2,
                                                  "rtcpDetectionInterval": 10,
                                                  "saveToConfig": true,
                                                  "sendDummyPayload": false,
                                                  "sendRenewStream": false,
                                                  "spsBytes": "",
                                                  "ssmIp": "",
                                                  "swfUrl": "",
                                                  "tcUrl": "",
                                                  "tos": 256,
                                                  "ttl": 256,
                                                  "uri": "rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4",
                                                  "videoSourceIndex": "high"
                                        },
                                        "queryTimestamp": 1508320789466.095,
                                        "serverAgent": "FMS/3,5,7,7009",
                                        "swfUrl": "rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4",
                                        "tcUrl": "rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4",
                                        "type": "INR",
                                        "typeNumeric": 5282249572905648000,
                                        "uniqueId": 59,
                                        "upTime": 35224.0149,
                                        "video": {
                                                  "aveFrameRate": 26.6774,
                                                  "aveKeyFramesPerSec": 0.4839,
                                                  "aveVideoBitRate": 1053309.6774,
                                                  "bytesCount": 4407924,
                                                  "codec": "VH264",
                                                  "codecNumeric": 6217274493967008000,
                                                  "currFrameRate": 25.3333,
                                                  "currKeyFramesPerSec": 0.3333,
                                                  "currVideoBitRate": 1299993.3333,
                                                  "droppedBytesCount": 0,
                                                  "droppedPacketsCount": 0,
                                                  "height": 306,
                                                  "level": 30,
                                                  "packetsCount": 940,
                                                  "profile": 66,
                                                  "width": 720
                                        }
                              }
                    ],
                    "description": "Available inbound streams",
                    "status": "SUCCESS"
          }
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - appName - EvoStream Media Server
  - audio – ストリームのオーディオ部分の統計情報
    - aveAudioBitRate - ストリームの先頭からのオーディオフレームの平均ビットレート
    - bytesCount - 受信したオーディオデータ総量
    - codec - オーディオcodec名
    - codecNumeric - 内部使用コード
    - currAudioBitRate - コマンドコール時点で最後のオーディオフレームのビットレート
    - droppedBytesCount - ロストしたビデオバイト数
    - droppedPacketsCount – ロストオーディオパケット数
    - packetsCount – 受信オーディオパケット総数
  - bandwidth – ストリームの現在の使用帯域
  - connectionType - 1=pull, 2=push, 3=HLS, 4=HDS, 5=MSS, 6=DASH, 7=record, 8=launchprocess, 9=webrtc, 10=metadata, 0=standard
  - canDropFrames – *アウトストリームのみ*  クライエントによりセットされるフラグでフレーム／パケット落ちを許す
  - creationTimestamp – ストリーム生成時点のUNIXタイムスタンプ。UNIXタイムはUNIXエポック(1970年1月1日)からの秒数です
  - edgePid – クラスタリング用の内部使用フラグ
  - farIp - far側のIPアドレス
  - farPort - far側の使用ポート
  - ip - ソースストリームホストのIPアドレス
  - inStreamUniqueID – *プッシュストリーム*のソースストリームid
  - name – ストリームの`localStreamName`
  - nearIp - ローカルコンピューターで使用されるIPアドレス
  - nearPort - ローカルコンピューターで使用されるポート
  - outStreamsUniqueIDs – *プルストリームの際* 入力ストリームに関連する出力ストリームIDのアレイ
  - pageUrl - リクエスト元のページへのリンク
  - port - serviceにバインドされたポート
  - processID - APIコマンドを処理するEMSインスタンスのプロセスID
  - processType - APIコマンドを処理するEMSインスタンスにより、Origin または edge
  - queryTimestamp – リクエストがクエリーされた時間のタイムスタンプ(UNIX時間)
  - serverAgent - 使用されたサーバーエージェント
  - type – ストリームタイプ。重要な情報は最初の２文字:
    - char 1 = インバウンドはI、アウトバウンドは O
    - char 2 = ネットワークはN、 ファイルはF
    - char 3+ = ストリームに関する詳細情報
      example: INR = Inbound Network Stream (a stream coming from the network into the EMS)
  - typeNumeric - ストリームタイプ文字に0で埋めて8バイトにした配列から得られる数値
  - uniqueId – ストリームのuniqueID(整数値)
  - upTime – ストリームがaliveかつ実行中の期間(秒数)
  - emulateUserAgent – EMSが他のサーバーと自身を区別するために使用する文字列。EMSが自身をFlash Media Serverと指定する等に使用可能です
  - video – ストリームのビデオ部分の統計情報
    - aveFrameRate- ストリーム開始からの平均フレームレート
    - aveKeyFramesPerSec - ストリーム開始からの平均毎秒キーフレーム
    - aveVideoBitRate -  ストリーム開始からのビデオフレームの平均ビットレート
    - bytesCount - 受信ビデオデータ総量
    - codec - ビデオcodec名
    - codecNumeric - 内部使用コード
    - currFrameRate - 秒あたりで処理されているビデオフレーム数
    - currKeyFramesPerSec - 秒あたりで処理されるビデオキーフレーム数
    - currVideoBitRate - コマンドコール時点の最後のビデオフレームのビットレート
    - droppedBytesCount – ロストしたビデオバイト数
    - droppedPacketsCount – ロストしたビデオパケット数
    - height - ビデオストリームの縦ピクセル数
    - level - H264レベル
    - packetsCount – ビデオパケット受信総数
    - profile - H264プロファイル
    - width - ビデオストリームの横ピクセル数

- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [listInboundStreamNames](listInboundStreamNames.html)