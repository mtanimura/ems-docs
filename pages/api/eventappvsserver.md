---
title: Application vs. Server Events
keywords: events
sidebar: api_sidebar
permalink: eventappvsserver.html
folder: api
toc: false
---

config.luaファイルは次の2つのeventLoggerセクションを持ちます

1. **Application-owned** – application configurationセクションに記述があります。“application level”イベントを設定します。This is lower in the file and is “inside” the application configuration section. It configures “application level” events. **ここは編集して設定変更を行って結構です**

   ​

2. **Server-wide** (またはデフォルト) – ファイルの上の方の変数スコープの外側に記述があります。アプリケーションの外やアプリケーションレベルでは補足できないイベントの設定です。ほとんどがサーバー起動やシャットダウン、アプリケーションの読み込みなどシステムイベント



## 関連リンク

- [Event Overview](eventoverview.html)
- [Configuring Event Notifications](eventnotification.html)
- [Event Sinks](eventsinks.html)
- [Events List](eventlist.html)
- [Event Definition](eventdefinition.html)
- [Event Logger](userguide_configlua.html#eventLogger)
- [EvoWebservices Event](evowebservices_event.html)
- [EvoWebservices Event Configuration](evowebservices_eventconfiguration)

