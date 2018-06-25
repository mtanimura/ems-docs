---
title: イベント通知システム
keywords: webservices
sidebar: evowebservices_sidebar
permalink: evowebservices_event.html
folder: evowebservices
toc: false
---

EMSイベント通知システムをつかえば、非常にパワフルにEMSとのインタラクションを行うことができます。サーバーの使用状況に関する理解や監視が簡単に行えます。ログファイルのポーリングやパースを行ったり、EMSから出力されたHTTPベースの通知をサブスクライブすることができます。

モニタリング監視や測量的解析が行えるだけでなく、イベント通知システムを利用して**カスタムストリーミング処理を作成**することもできます。新規インバウンドストリームからHLSやHDSやDASHストリームを自動的に生成するには、各“**new inbound stream**”に対して、`createHLSStream`, `createHDSStream` or `createDASHStream`をコールするだけです。
関連するアウトバウンドストリームがなくなった時に、自動的にインバウンドストリームをクローズしたい場合は、“**outbound stream closed**”イベント受け取り時に`shutdownStream`をコールします。


## Web Servicesで使用されるイベントのリスト

次のイベントがEMSにより生成されます:

- **inStreamCreated** – インバウンドストリームが生成された
- **inStreamClosed** – インバウンドストリームがクローズされた
- **outStreamCreated** – 新規アウトバウンドストリームが生成された
- **outStreamClosed** – アウトバウンドストリームがクローズされた
- **timerTriggered** – タイマーイベント
- **hdsMasterPlaylistUpdated** – HDS group manifestが変更された
- **hdsChildPlaylistUpdated** – ストリームに固有のHDS manifestが変更された
- **hdsChunkClosed** – 新規HDS segmentが完了し、ディスク上でreadyとなった
- **hdsChunkDeleted** - HDSチャンクが削除された
- **hlsMasterPlaylistUpdated** – HLS group プレイリストが変更された
- **hlsChunkClosed** – 新規HLS segmentが完了し、ディスク上でreadyとなった
- **hlsChunkDeleted** - HLS chunkが削除された
- **dashPlaylistUpdated** - DASH manifestが変更された
- **dashChunkClosed** - 新規DASH fragmentが完了し、ディスク上でreadyとなった
- **dashChunkDeleted** - DASHチャンクが削除された

------

## 関連リンク

- [Event Overview](userguide_eventsoverview.html)
- [Events List](userguide_eventslist.html)
- [Event Definition](userguide_eventsdefinition.htmll)