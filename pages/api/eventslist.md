---
title: Event List
keyword: events
sidebar: api_sidebar
permalink: eventlist.html
folder: api
toc: true
---

## ストリームイベント

|         イベント          | 内容                              |
| :--------------------: | ---------------------------------------- |
|    inStreamCreated     | 新規インバウンドストリームが生成されました    |
|    outStreamCreated    | 新規アウトバウンドストリームが生成されました   |
|     streamCreated      | 新規中間ストリーム(inでもoutでもない)が生成されました |
|     inStreamClosed     | インバウンドストリームがクローズされました        |
|    outStreamClosed     | アウトバウンドストリームがクローズされました       |
|      streamClosed      | 中間ストリームがクローズされました         |
| inStreamCodecsUpdated  | インバウンドストリームのオーディオ／ビデオが確認または変更されました |
| outStreamCodecsUpdated | アウトバウンドストリームのオーディオ／ビデオが確認または変更されました |
|  streamCodecsUpdated   | 中間ストリームのオーディオ／ビデオが確認または変更されました |
|    audioFeedStopped    | オーディオフィードが一定時間以上停止しました |
|    videoFeedStopped    | ビデオフィードが一定時間以上停止しました |



## Adaptiveストリーミング/File-basedストリーミングイベント

|          イベント           | 内容                              |
| :----------------------: | ---------------------------------------- |
| hlsChildPlaylistUpdated  | ストリームに特定のHLSプレイリストが更新されました |
| hlsMasterPlaylistUpdated | HLSグループプレイリストが更新されました     |
|     hlsChunkCreated      | 新規HLSセグメントがオープンされました     |
|      hlsChunkClosed      | 新規HLSセグメントが完了し、ディスク上でReadyとなりました |
|      hlsChunkError       | HLSセグメントファイル書き込み時にエラーが起きました |
|     hlsChunkDeleted      | HLSチャンクが削除されました                 |
| hdsChildPlaylistUpdated  | ストリームに特定のHDS manifestが更新されました |
| hdsMasterPlaylistUpdated | HDSグループmanifestが更新されました |
|     hdsChunkCreated      | 新規HDSセグメントファイルがオープンされました |
|      hdsChunkClosed      | 新規HDSセグメントが完了し、ディスク上でReadyとなりました |
|      hdsChunkError       | HDSセグメント/フラグメントファイル書き込み時にエラーが起きました |
|     hdsChunkDeleted      | HDSチャンクが削除されました |
|     mssChunkCreated      | 新規MSSフラグメントファイルがオープンされました |
|      mssChunkClosed      | 新規MSSフラグメントが完了し、ディスク上でReadyとなりました |
|      mssChunkError       | MSSフラグメントファイル書き込みじにエラーが起きました |
|    mssPlaylistUpdated    | MSS manifest が更新されました           |
|     dashChunkCreated     | 新規DASHフラグメントファイルがオープンされました |
|     dashChunkClosed      | 新規DASHフラグメントが完了し、ディスク上でReadyとなりました |
|      dashChunkError      | DASHフラグメントフィアル書き込み時にエラーが起きました |
|     dashChunkDeleted     | DASHチャンクが削除されました                 |
|   dashPlaylistUpdated    | DASH manifestが更新されました |
|    recordChunkCreated    | 新規MP4フラグメントがオープンされました |
|    recordChunkClosed     | 新規MP4フラグメントが完了し、ディスク上でReadyとなりました |
|     recordChunkError     | MP4ファイル書き込み時にエラーが起きました |



## Web Serverイベント

|          イベント          | 内容                            |
| :---------------------: | -------------------------------------- |
| streamingSessionStarted | ストリーミングセッションが開始されました |
|  streamingSessionEnded  | ストリーミングセッションが完了しました |
|   mediaFileDownloaded   | ファイルダウンロードが完了しました |



## API Based イベント

|     イベント     | 内容                              |
| :------------: | ---------------------------------------- |
|   cliRequest   | EMSがランタイムAPIコマンドを受信しました |
|  cliResponse   | 直前のランタイムAPIコマンドにたいしてEMSがレスポンスを生成しました |
| processStarted | `launchProcess` APIコマンドリクエストによりプロセスが開始しました |
| processStopped | `launchProcess` APIコマンドで開始されたプロセスが停止しました |
|  timerCreated  | `setTimer` APIコマンドにより新規タイマーが生成されました |
| timerTriggered | リクエストされたタイマーイベント |
|  timerClosed   | タイマーがクローズし、以降`timerTriggered`イベントは生成されません |



## Connection Based イベント

|           イベント            | 内容                              |
| :-------------------------: | ---------------------------------------- |
|   protocolRegisteredToApp   | 接続が確立されました |
| protocolUnregisteredFromApp | 接続が切断されました |
|       carrierCreated        | TCPソケットなどなんらかのIOハンドラが生成されました。 接続の生成とは異なります |
|        carrierClosed        | UDPソケットなどなんらかのIOハンドラがクローズされました。接続のクローズとは異なります |
|      playlistItemStart      |                                          |
|   firstPlaylistItemStart    |                                          |
|    lastPlaylistItemStart    |                                          |
|        webRTCStarted        |                                          |
|        webRTCStopped        |                                          |
| webRTCPeerConnectionCreated |                                          |
| webRTCPeerConnectionClosed  |                                          |
|   webRTCPeerStreamStarted   | WebRTC新規ストリームがオープンされました |
|   webRTCPeerStreamClosed    | WebRTCストリームクローズされました       |
|    webRtcServiceStarted     | WebRTC serviceが開始しました             |
|    webRtcServiceStopped     | WebRTC serviceが停止しました             |
|     webRtcPeerConnected     |                                          |
|   webRtcPeerDisconnected    |                                          |
|       webRtcPeerError       |                                          |
|       WSStreamStarted       | WebSocket新規ストリームがオープンされました  |
|       WSStreamClosed        | WebSocketストリームがクローズされました  |



## Application Based イベント

|      イベント      | 内容                              |
| :--------------: | ---------------------------------------- |
| applicationStart | 内部EMSアプリケーションが開始しました |
| applicationStop  | 内部EMSアプリケーションが停止しました。シャットダウンが間もなく起こることを示しています |
|  serverStarted   | EMSが開始しました |
|  serverStopping  | EMSがシャットダウンします。シャットダウン完了直前に発せられます |

------

The data definitions for each event can be found below. The specific schema for each event will depend up on the `serializerType` chosen for your Event Notification Sink (defined earlier in this document).


------

## 関連リンク

- [Events Overview](eventsoverview.html)
