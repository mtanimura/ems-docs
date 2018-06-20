---
title: Configuring EMS Event Notifications
keywords: webservices
sidebar: evowebservices_sidebar
permalink: evowebservices_eventconfiguration.html
folder: evowebservices
toc: false
---

EMSイベント通知はEMS Web Servicesと通信できるよう設定しておく必要があります。EMS設定ファイルを下記の要領で編集してください。
イベント通知の設定に関して詳しくは [Configuring Event Notification](userguide_eventsoverview.html#configuring-event-notificationl) を参照してください。 




**config.lua:**

```
eventLogger=
{
  sinks=
  {
    {
      type="RPC",
      url="http://127.0.0.1:4000/evowebservices/",
      serializerType="JSON",
      enabledEvents=
      {
		"inStreamCreated",
		"inStreamClosed",
		"outStreamCreated",
		"outStreamClosed",
		"timerTriggered",
		"hdsMasterPlaylistUpdated",
		"hdsChildPlaylistUpdated",
		"hdsChunkClosed",
		"hdsChunkDeleted",
		"hlsMasterPlaylistUpdated",
		"hlsChunkClosed",
		"hlsChunkDeleted",
		"dashPlaylistUpdated",
		"dashChunkClosed",
		"dashChunkDeleted",
      },
    },
  },
},
```

**enabledEvents** パラメーターでは、どのイベントを受信するかを特定することができますが、リストの追加・削除は推奨しません。イベントが無いとサービスが正常に動作しません。

evowebservicesはEMSイベントに依存します。

- **RPC – リモートプロシージャコール**

  イベントの詳細がHTTP POST経由でリモートホストに伝送されます。EMSはリモートホストからのレスポンスを無視します。

  RPC sink 設定:

  ```
  type="RPC",
  url="http://localhost:4000/evowebservices/",
  serializerType="JSON"
  ```

  urlフィールドはイベント通知HTTP POSTを受信する宛先を設定します。EMSが実行しているのと同じコンピュータ("localhost")上にweb sevicesインストールされている場合の例が以下に記述されています。web serviceが実行されているコンピュータのIPアドレスはに適宜変えてください。

- **serializerType**

  イベントログフォーマット serializerTypeはJSON, XML, XMLRPCなどのフォーマットがとれます

  JSONフォーマットでの例:

  ```
  {"payload":{"creationTimestamp":1349335053486.4370,"name":"","queryTimestamp":1349335053487.4370,"type":"NR","uniqueId":1,"upTime":1.0000},"type":"streamCreated"}
  ```


------

## 関連リンク

- [Event Overview](userguide_eventsoverview.html)
- [Events List](userguide_eventslist.html)
- [Event Definition](userguide_eventsdefinition.htmll)