---
title: stopWebRTC
keywords: api
sidebar: api_sidebar
permalink: stopWebRTC.html
folder: api
toc: false
---

ERS(Evostream Rendezvous Server)のWebRTC Signallingクライエントを停止します。



## API パラメータ


パラメータはありません



## API Call テンプレート

```
stopwebrtc
```



### JSONのSuccess Response

```
{
"data":{
    "ersip":"52.6.14.61",
    "ersport":3535,
    "roomid":"testRoom"
},
"description":"Stopped WebRTC Negotiation Service",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data– パースするデータはありません
  - ersip – ERSのipアドレス
  - ersport – ERSのポート
  - roomId – roomid
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

-  [startWebRTC](startWebRTC.html)
-  [WebRTC Overview](html5players_wrtcoverview.html)