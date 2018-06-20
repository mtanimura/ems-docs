---
title: Release Notes
keywords: release notes
sidebar: home_sidebar
permalink: /home_releasenotes.html
folder: home
toc: false
---

# EMS 2.0.1

## バグfix

- 不正アクセスを防ぐため、UIのログインページからGoogleおよびFacebookアカウントログインオプションを削除
- ウインドウズでエイリアスを用いたVODファイルの再生ができない問題を修正
- UIセキュリティの向上のためにangularが使用できるAPIを制限
- EMSがデーモンクラスタモード動作時のRTMPストリーム再生の修正
- Edgeブラウザでバッファクリアリング(低遅延維持)が再生をスキップする問題の修正
- API explorer内のAPI名やダッシュボードのポート番号入力の修正等のマイナーなUIの改善


# EMS 2.0.0

## ハイライト

- HEVC/H.265 のサポート - HLS および DASHの再生
- 新しいWeb UI - Node.jsベースでのEMS APIへのフルアクセス
- 新しいNode.jsベースのEvo-Webserver
- 全てのプロトコルでIPv6をサポート
- ブラウザ、iOS、Android向けのIntegration ready playerライブラリ
- `<video>`タグによるダイレクト再生、プレーヤー不要
- Raspberry-Piでのハードウェアトランスコード


------

## 新機能

- Android/iOS ピアツーピア(WebRTC)再生でSRTPを使用
- HTML5イベントによるブラウザプレーヤーとのインテグレーションの向上
- web service使用例をJavascriptで書き換え
- WebRTCおよびWebsocket/HTML再生におけるサーバーサイドプレイリストのサポート
- WebRTCおよびWebsocket/HTML再生におけるLazy-Pullのサポート
- WebRTC接続でTCP TURNが使用可
- ブラウザおよびEMS接続においてTLS暗号化ERS通信
- COTURNのサポート、その他のSTUN/TURNサーバーのサポート
- websocket経由でのメタデータ配信


------

## 新しいAPI

- addMetadataListener - オンザフライでメタデータlistenerの追加
- listMetadataListeners - メタデータingestion pointのリスト表示
- getInboundStreamsCount - GetStreamCountよりもより正確なメソッド
- getLicenseId - 新しいUIで使用するライセンスidをプログラム的に取得


------

## 新しいイベント

- hdsChunkClosed
- hlsChunkClosed
- dashChunkClosed
- webRtcServiceStarted
- webRtcServiceStopped


------

## バグfix

- ログファイルのローリング機能をより適切に
- HTTP-ProxyのURLパラメータ区切りに"%3f"ではなく"?"を使用
- WebsocketおよびWebRTCブラウザプレーヤーの大幅な改善
- 接続断の際、適切にERS接続リトライ
- 大きなキーフレームのトリムを防止するためのconfig.luaにRTSPバッファ変数の追加
- アウトバウンドRTP/RTSPストリームのFUA問題の修正
- MPEG-TSプッシュの際のランダムなストリーム名の修正
- DASHで稀に発生するビデオ・オーディオの同期ズレ問題の修正
- createHLSStreamコマンドでのプレイリスト名およびchunkbasenameパラメータ処理の修正
- オーディオ・ビデオのみHLSの修正
- mp4writerが大容量ファイルを扱う際の問題の修正

