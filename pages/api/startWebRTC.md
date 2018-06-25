---
title: startWebRTC
keywords: api
sidebar: api_sidebar
permalink: startWebRTC.html
folder: api
toc: false
---

ERS (Evostream Rendezvous Server)に向けてWebRTCシグナリングクライエントを開始します

与えられたIPアドレスのポートをオープンし、evowrtcclient.htmlを使用してアクセスできるroomIDを開きます。



## API パラメータ


| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :----: | :-------: | :-----------: | ---------------------------------------- |
|     ersIp      | 文字列 |   true    |    *null*     | ERSのIPアドレス          |
|    ersPort     | 文字列 |   true    |    *null*     | ERSがlistenしているポート |
|     roomId     | 文字列 |   true    |    *null*     | クライエントブラウザがESMに接続するのに使用されるERSのroom ID |
|     token      | 文字列 |   false   |    *null*     | ERS内で使用されるセキュリティトークン |



## API Call テンプレート

```
startWebrtc ersip=<ERS_IPAddress> ersport=<ERS_Port> roomid=<roomID>
```



### サンプル API Call

```
startWebrtc ersip=52.6.14.61 ersport=3535 roomid=testRoom
```



### JSONのSuccess Response

```
{
          "data": {
                    "data": {
                              "configId": 2,
                              "ers": "",
                              "ersOverSsl": false,
                              "ersip": "54.174.188.145",
                              "ersport": 4545,
                              "keepAlive": true,
                              "name": "evostreamms",
                              "operationType": 9,
                              "roomid": "testRoom",
                              "sslCert": "../config/server.cert",
                              "sslKey": "../config/server.key",
                              "token": ""
                    },
                    "description": "Started WebRTC Negotiation Service",
                    "status": "SUCCESS"
          }
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ

  - configId - コマンドのconfigID
  - ers - ERS名
  - ersOverSsl - SSL設定
  - ersip – ERSのIPアドレス
  - ersport – ERSがlistenするポート
  - keepAlive - `keepAlive`がtrueの場合、接続が切断した際EMSは再接続します
  - name - ERSを使用するアプリケーション名
  - operationType – オペレーションタイプ（内部使用）
  - roomId – room ID
  - sslCert - SSL証明書
  - sslKey - SSLキー証明書
  - token - ERS内で使用されるセキュリティトークン
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## Notes

- Room IDは一回のみ開始できます


------

## 関連リンク

- [stopWebRTC](stopWebRTC.html)
- [WebRTC Overview](html5players_wrtcoverview.html)