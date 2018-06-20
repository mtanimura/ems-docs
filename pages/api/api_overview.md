---
title: Overview
keywords: api
sidebar: api_sidebar
permalink: api_overview.html
folder: api
toc: false
---

本文書はEvostream Media Server(EMS)のApplication Programming Interface (API)およびイベント通知システム(Event Notification System)について記述されています。

手動およびプログラムによるEMSとの双方向RESTful APIによるインタラクションを行えます。シンプルなWebサービスおよびスクリプトを作ってEMSの機能を拡張したり希望のロジックを構築することができます。

APIは２つのパートにより成り立ちます。EMSにコールして使用できるのが**API**で、EMSで何が起きているか通知し返すのが、**イベント通知システム**です。

APIをつかってランタイムでサーバーの挙動を変更制御することができます。新規ストリームを取得したり生成したり、ストリームや接続に関する情報を返したり、稼働中のサービスをスタートしたりストップしたりといった様々なことをサーバーに行わせることができます。
[イベント通知システム](eventsoverview.html)は、新規ストリームが生成された、ストリームがドロップした、サーバーが停止したといった、EMS内で起きた特定イベントをユーザに通知する手段を提供します。

これらAPIの２つの側面を利用して、複雑なロードバランシングやカスタムストリーミングワークフロー、ストリームトラフィックの暗号化や保護といったことを、簡易で効率的なweb serviceやスクリプトを用いてオンザフライで行えます。

EvoStreamはAPIを活用したweb serviceのサンプル集を提供しています。Evostreamの[サイト](https://evostream.com/software-downloads/)からダウンロードすることができ、そのまま使用したり、プロジェクトに合わせて書き換えて使用することもできます。
