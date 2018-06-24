---
title: Overview
keywords: webservices
sidebar: evowebservices_sidebar
permalink: evowebservices_overview.html
folder: evowebservices
toc: false
---


本文書はEvoStream Media Server (EMS) Web Serviceの使い方に関して記述されています。webサービスの起動をはじめ設定ファイルの編集をともなう高度な内容もカバーされています。

本文書はEMS Web Servicesのユーザー向けに書かれています。マルチメディアストリーミングおよび関連技術について基礎的な理解がある前提です。

## WEMS Web Servicesとは?

EMS Web Servicesはwebサーバーならどれでも取り扱いができるスクリプト一式で、EMSのイベント通知システムやランタイムAPIを利用します。
EMS Web Servicesをつかってユーザーのニーズや環境に合わせてEMSに拡張機能を与え、カスタマイズすることができます。

## なぜEMS Web Servicesをつかうのか?

EMS Web Servicesは、EMSイベント通知システムおよびランタイムAPIを使ってカスタムストリーミング処理を行えるツールです。スクリプト（APIコールをHTTPインターフェースコール用にラッピングしたものとして機能）は実運用環境でお使いいただけるもので、用途にあわせて編集して使うことができます。web servicesのソースコードが提供されていますので、自在に編集して機能を拡張してお使いいただけます。

## どのように動作するのか?

EMS Web ServicesはEMS通知システムと協調動作し、ストリーミングオートメーションを生成するEMS Runtime APIを扱える一連のwebアプリケーションスクリプトです。各web serviceは特定の機能を提供し、組み合わせて使うことで複合的な結果を生み出すことができます。

## システム条件

- **オペレーティングシステム条件**

  EMS Web ServicesはEMSと同じコンピュータ上または離れた別のコンピュータ上で実行することができます。EMS Web SerivesはWindows®, Linux, Mac OSXのどれでも実行可能です。

- **システム最低条件**
  - 700 MHz以上のプロセッサ
  - 128MBのメモリ (システムメモリ)
  - 10MB以上のストレージ空き容量
  - Web Server (.phpスクリプトを使用する場合)
  - Node.js (.js スクリプトを使用する場合)
  - インターネットアクセス


