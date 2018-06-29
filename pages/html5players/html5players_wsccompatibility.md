---
title: ブラウザ互換性
keywords: websocket
sidebar: html5players_sidebar
permalink: emscloud_wscompatibility.html
folder: emscloud
toc: false
---

下図はさまざまなブラウザとEvoStream WebSocket機能の互換性対応表です

![](/images/html5/ws_compatibility.JPG)



**Firefox設定変更**

危険性を承知の上で使用する
The following configuration changes must be made to Firefox before it will work with HTML5 playback and Peer to Peer:

- アドレスフィールドに入力してEnter: about:config
  -“危険性を承知の上で使用する”をクリックしてください
次の設定名の値を確認してください:
  - media.mediasource.enabled = true
  - media.mediasource.whitelist = false
  - media.mediasource.mp4.enabled = true
  - media.fragmented-mp4.exposed = true
  - media.fragmented-mp4.ffmpeg.enabled = true
  - media.fragmented-mp4.gmp.enabled = true
  - media.fragmented-mp4.use-blank-decoder = false

- 設定変更を適用するためFirefoxを再起動してください




## Notes

ブラウザがHTML5プレーヤーをサポートしているか確認するには下記リンクを参考にしてください:

- https://html5test.com/
- https://www.youtube.com/html5?gl=PH