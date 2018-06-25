---
title: EMSインテグレーションReadyプレーヤーライブラリ
keywords: js
sidebar: html5players_sidebar
permalink: html5players_emsjslib.html
folder: html5players
toc: false
---

下記はブラウザ、iOS、Androidで使用可能なサンプルコード(EMS JS libraries)です

```
<html>
 <head>
  <script src="./js/evohtml5player-latest.bundle.js"></script>     <--(1) EvoStream JSPlayer Bundleをインポート
	:
	:
	:
 </head>
 <body>
	:
	:
	<video id="myVideo"></video>     <--(2) ビデオタグをdeclare　正しいエレメントIDが割り当てられているかを確認
	:
	:

	<script>
	 function playViaWebSocket() {     <--(3) WebSocket経由でストリーム再生したい場合にコールする
	 var options = {
		emsIp: "192.168.10.10", // EMSインスタンスのIPアドレス
		streamName: "myStream", // 再生したいストリーム
		videoTagId: "myVideo"   // ビデオタグのエレメントID
	     };
		var emsPlayer = new EvoWsPlayer ( options );
		emsPlayer.play();
	  }

	 function playViaWebRtc() {     <-- (4) WebRTCをつかってストリーム再生したい場合にコールする
	 var options = {
		emsIp: "10.10.20.30",     // ERSのIPアドレス
		port:  4545,			// ERSに設定したポートを設定してください
		streamName: "myStream",	  // 再生したいストリーム
		videoTagId: "myVideo"     // ビデオタグのエレメントID
		roomName: "myRoom",	      // EMSに設定されているroom
          };
		var emsPlayer = new EvoWrtcPlayer ( options );
		emsPlayer.play();
	  }

	</script>
 </body>
</html>
```
