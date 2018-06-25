---
title: プレーヤーイベント
keywords: events
sidebar: html5players_sidebar
permalink: html5players_playerevents.html
folder: html5players
toc: false
---

プレーヤーイベントを受信するには、`EvoWSPlayer` または `EvoWrtcPlayer`の`registerEventListener`メソッドをコールし、`eventName`と`eventData`の２つのパラメータを受信するハンドラに渡してください。すべてのイベントが`eventData`を持つとは限りません。

**例:**

```
var player = new EvoWsPlayer ( options ) ;
player.registerEventListener ( function (event,description){
                    if ( event == 'transportclosed' ) {
                        // do something...etc.
                    }
                });
```



### イベントリスト

**プレーヤーイベント**

|  イベント名   | 内容                              |
| :-----------: | ---------------------------------------- |
| playerStarted | プレーヤーがストリーム再生を始めたら発行 |
| playerStopped | プレーヤーが意図的に停止されたら発行(ストップボタンが押されたり接続がロストした等) |
| playerFroze  | 無効なデータやパケットロストその他の事由でプレーヤーが再生に失敗した際に発行。おそらく事前にhaltイベントに対する時間的しきい値が設けられています |
| playerNoData  | ストリーミングチャンネルにデータが無い |
| playerResume  | 一時停止またはhaltイベントから再生を再開したら発行 |
| playerPause  | プレーヤーが意図的に一時停止状態に置かれた場合に発行(現状はこのような状態に置かれることはありませんが、将来的に必要になります) |



**接続メッセージ (WebSockets)**

|      イベント名      | 内容                              |
| :------------------: | ---------------------------------------- |
| transportEstablished | ESM/サーバーへの接続が確立された際に発行 |
|    transportError    | EMSへの接続エラーの際に発行 |
|   transportClosed    | EMSへの接続が意図的にまたはエラーでクローズされた際に発行 |



**WebRTC ステート**

|    イベント名     | 内容                              |
| :---------------: | ---------------------------------------- |
|    joinedRoom     | プレーヤーがERSに接続            |
|    createdPeer    | Local peering candidatesが生成された |
|   checkingPeer    | Remote peering candidatesが受信され、接続試行が開始された |
|  chosenCandType   | peering candidateタイプが: hostまたはreflexまたはrelay |
|   connectedPeer   | peerへのルートが確立され、ストリーミングスタックがセットアップされた |
| disconnectedPeer  | 接続したpeerから接続断となった |
| connectFailedPeer | peerに接続不可            |
|     closePeer     | Peering stackが消滅                 |



**Platform/Player Errors**

| イベント名  | 内容                              |
| :---------: | ---------------------------------------- |
| playeralert | プレーヤー側のロジックからエラーが生成された。例: ”ビデオエレメントが見つからない”、”MediaSouce APIが有効化されていないまたはサポートされていない”等 |
| playererror | プレーヤー側からのエラー。プラットフォームにより内容は異なります。例: AppendBufferの問題(プレーヤー側のエラー)、メディアデコードエラー等 |



**QOS レポート**

|    イベント名     |            Value             | 内容                              |
| :---------------: | :--------------------------: | ---------------------------------------- |
|   rep-frameloss   |       フレームロスカウント   | 1秒に1回発行される秒間に置きたドロップ／ロストフレーム数 |
| rep-estthroughput | 予想スループット kbps | 1秒に1回発行される演算インジェストデータ量 |



**QOS Accessor Functions**

|    イベント名    | 内容                              |
| :--------------: | ---------------------------------------- |
| getAggFrameLoss  | 総フレームロス取得関数 |
| getAggPacketLoss | 総パケットロス取得関数 |

