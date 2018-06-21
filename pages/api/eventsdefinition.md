---
title: Events Definition
keyword: events
sidebar: api_sidebar
permalink: eventsdefinition.html
folder: api
toc: true
---



## ストリームイベント

### inStreamCreated, outStreamCreated, streamCreated

インバウンド、アウトバウンド、中間ストリームが生成された

```
appName: evostreamms
    audio:
        bytesCount: 0
        codec: AUNK
        codecNumeric: 4707755069515235328
        droppedBytesCount: 0
        droppedPacketsCount: 0
        packetsCount: 0
    bandwidth: 0
    connectionType: 1
    creationTimestamp: 1361182998409.229
    ip: 192.168.1.130
    name: test
    port: 49730
    pullSettings:
        audioCodecBytes:
        configId: 1
        emulateUserAgent: EvoStream Media Server (www.evostream.com) player
        forceTcp: false
        isAudio: true
        keepAlive: true
        localStreamName: test
        operationType: 1
        pageUrl:
        ppsBytes:
        rtcpDetectionInterval: 10
        spsBytes:
        ssmIp:
        swfUrl:
        tcUrl:
        tos: 256
        ttl: 256
        uri: rtmp://cp76072.live.edgefcs.net/live/MED-HQ-Flash@42814
    queryTimestamp: 1361182998424.829
    type: INR
    typeNumeric: 5282249572905648128
    uniqueId: 2
    upTime: 15.600
    video:
        bytesCount: 0
        codec: VUNK
        codecNumeric: 6220964544311721984
        droppedBytesCount: 0
        droppedPacketsCount: 0
        packetsCount: 0
```

- appName – ストリームを使用するアプリケーション名

- audio – オーディオストリームの統計情報

- bandwidth – ストリームの帯域

- connectionType – ストリーム接続タイプ

- creationTimestamp – ストリームが生成されたエポックタイムスタンプ (1/1/70からのmsec)

- ip – ストリームに使用されるIPアドレスIP

- nearIP – ホストコンピューターのアドレス

- farIP – ストリームソースのIP

- name – ストリームに割りあてられた名前

- port – ストリームに使用されるポート

- nearPort – ホストコンピューターに使用されるポート

- farPort – ストリームソースに使用されるポート

- pullSettings – `pullstream`設定 *pullStream APIコマンドでプルされたインバウンドストリームのみ*

- queryTimestamp – ストリームがクエリーされたエポックタイムスタンプ(1/1/70からのmsec)

- record – ストリームのRecord設定

- type – プロトコルタイプ

- typeNumeric – 10進数表記でのプロトコルタイプ

- uniqueId – ストリームID

- upTime – ミリ秒単位のストリームデュレーション

- video – ビデオストリームの統計情報







### inStreamClosed, outStreamClosed, streamClosed

インバウンド、アウトバウンド、中間ストリームがクローズされた

```
appName: evostreamms
	audio:
		bytesCount: 190351
		codec: AAAC
		codecNumeric: 4702111241970122752
		droppedBytesCount: 0
		droppedPacketsCount: 0
		packetsCount: 681
	bandwidth: 548
	connectionType: 1
	creationTimestamp: 1361182998409.229
	ip: 192.168.2.88
	name: test
	outStreamsUniqueIds:
		0: 3
	port: 49730
	pullSettings:
		audioCodecBytes:
		configId: 1
		emulateUserAgent: EvoStream Media Server (www.evostream.com) player
		forceTcp: false
		isAudio: true
		keepAlive: true
		localStreamName: test
		operationType: 1
		pageUrl:
		ppsBytes:
		rtcpDetectionInterval: 10
		spsBytes:
		ssmIp:
		swfUrl:
		tcUrl:
		tos: 256
		ttl: 256
		uri: rtmp://cp76072.live.edgefcs.net/live/MED-HQ-Flash@42814
	queryTimestamp: 1361183030139.685
	type: INR
	typeNumeric: 5282249572905648128
	uniqueId: 2
	upTime: 31730.456
	video:
		bytesCount: 2346717
		codec: VH264
		codecNumeric: 6217274493967007744
		droppedBytesCount: 0
		droppedPacketsCount: 0
		packetsCount: 1147
```

- appName – ストリームに使用されるアプリケーション名

- audio – オーディオストリームの統計情報

- bandwidth – ストリームの帯域

- connectionType – ストリーム接続タイプ

- creationTimestamp – ストリームが生成されたエポックタイムスタンプ (1/1/70からのmsec)

- ip – ストリームに使用されるIPアドレスIP

- nearIP – ホストコンピューターのアドレス

- farIP – ストリームソースのIP

- name – ストリームに割りあてられた名前

- port – ストリームに使用されるポート

- nearPort – ホストコンピューターに使用されるポート

- farPort – ストリームソースに使用されるポート

- pullSettings – `pullstream`設定 *pullStream APIコマンドでプルされたインバウンドストリームのみ*

- queryTimestamp – ストリームがクエリーされたエポックタイムスタンプ(1/1/70からのmsec)

- record – ストリームのRecord設定

- type – プロトコルタイプ

- typeNumeric – 10進数表記でのプロトコルタイプ

- uniqueId – ストリームID

- upTime – ミリ秒単位のストリームデュレーション

- video – ビデオストリームの統計情報




### inStreamCodecsUpdated, outStreamCodecsUpdated, streamCodecsUpdated

新規インバウンド、アウトバウンド、中間ストリームが特定のcodecとともに同定された

```
appName: evostreamms
	audio:
		bytesCount: 0
		codec: AUNK
		codecNumeric: 4707755069515235328
		droppedBytesCount: 0
		droppedPacketsCount: 0
		packetsCount: 0
	bandwidth: 548
	connectionType: 1
	creationTimestamp: 1361182998409.229
	ip: 192.168.2.88
	name: test
	port: 49730
	pullSettings:
		audioCodecBytes:
		configId: 1
		emulateUserAgent: EvoStream Media Server (www.evostream.com) player
		forceTcp: false
		isAudio: true
		keepAlive: true
		localStreamName: test
		operationType: 1
		pageUrl:
		ppsBytes:
		rtcpDetectionInterval: 10
		spsBytes:
		ssmIp:
		swfUrl:
		tcUrl:
		tos: 256
		ttl: 256
		uri: rtmp://cp76072.live.edgefcs.net/live/MED-HQ-Flash@42814
	queryTimestamp: 1361182998456.029
	type: INR
	typeNumeric: 5282249572905648128
	uniqueId: 2
	upTime: 46.800
	video:
		bytesCount: 56
		codec: VH264
		codecNumeric: 6217274493967007744
		droppedBytesCount: 0
		droppedPacketsCount: 0
		packetsCount: 1
```

- appName – ストリームを使用するアプリケーション名

- audio – オーディオストリームの統計情報

- bandwidth – ストリームの帯域

- connectionType – ストリーム接続タイプ

- creationTimestamp – ストリームが生成されたエポックタイムスタンプ (1/1/70からのmsec)

- ip – ストリームに使用されるIPアドレスIP

- nearIP – ホストコンピューターのアドレス

- farIP – ストリームソースのIP

- name – ストリームに割りあてられた名前

- port – ストリームに使用されるポート

- nearPort – ホストコンピューターに使用されるポート

- farPort – ストリームソースに使用されるポート

- pullSettings – `pullstream`設定 *pullStream APIコマンドでプルされたインバウンドストリームのみ*

- queryTimestamp – ストリームがクエリーされたエポックタイムスタンプ(1/1/70からのmsec)

- record – ストリームのRecord設定

- type – プロトコルタイプ

- typeNumeric – 10進数表記でのプロトコルタイプ

- uniqueId – ストリームID

- upTime – ミリ秒単位のストリームデュレーション

- video – ビデオストリームの統計情報




### audioFeedStopped, videoFeedStopped

ビデオまたはオーディオパケットロストによりイベントがトリガされた

```
audioFeedStopped

videoFeedStopped
```

- streamId – ストリームID

- localStreamName – オーディオをロストしたストリーム名







### playlistItemStart, firstPlaylistItemStart, lastPlaylistItemStart

RTMPプレイリストアイテムが再生を開始した際に生成されるイベント

```
firstPlaylistItemStart
PID: 10796
playlistName: stream.lst

playlistItemStart
PID: 10796
playlistName: stream.lst

lastPlaylistItemStart
PID: 12268
playlistName: stream.lst
```

- PID: プロセスID

- playlistName - プレイリストファイル名




## Adaptive Streaming / File-based Streaming Events

### hlsChunkCreated, hdsChunkCreated, mssChunkCreated, dashChunkCreated

HLS/HDS/MSS/DASHチャンクファイルがディスク書き込み用にオープンされる際にトリガされるイベント

```
hlsChunkCreated
/evo-webroot/hls/stream1/segment_1362025844863_1362025844863\_14.ts


hdsChunkCreated
evo-webroot/hds/stream1/f4vSeg1-Frag1


mssChunkCreated
/evo-webroot/mss/stream1/video/524288/1413797685000.m4s


dashChunkCreated
/evo-webroot/dash/stream1/video/229376/1416464032000.fmp4
```

**file** – HLS/HDS/MSS/DASHチャンクファイル名



### hlsChunkClosed, hdsChunkClosed, mssChunkClosed, dashChunkClosed

HLS/HDS/MSS/DASHチャンクファイルがクローズされた際にトリガされるイベント

```
hlsChunkClosed
/evo-webroot/hls/stream1/segment_1362025844863_1362025844863_14.ts

hdsChunkClosed
/evo-webroot/hds/stream1/f4vSeg1-Frag1

mssChunkClosed
/evo-webroot/mss/stream1/video/524288/1413797685000.m4s

dashChunkClosed
/evo-webroot/dash/stream1/video/229376/1416464032000.fmp4
```

**file** – クローズしたHLS/HDS/MSS/DASHチャンクファイル名



### hlsChunkError, hdsChunkError, mssChunkError, dashChunkError

HLS/HDS/MSS/DASHチャンクファイル書き込みのエラー発生時にトリガされるイベント

```
Could not write video sample to /evo-webroot/hls/stream1/
segment_1362025844863_1362025844863_14.ts
```

- error – エラー内容




### hlsChildPlaylistUpdated, hdsChildPlaylistUpdated

HLSまたはHDSストリームのプレイリストが更新された際にトリガされるイベント

```
hlsChildPlaylistUpdated
/evo-webroot/hls/stream1/playlist.m3u8


hdsChildPlaylistUpdated
/evo-webroot/hds/stream1/stream1.f4m
```

**file** – 更新されたHLSまたはHDSプレイリスト名



### hlsMasterPlaylistUpdated, hdsMasterPlaylistUpdated

HLSまたはHDSグループプレイリストファイルが更新された際にトリガされるイベント

```
hlsMasterPlaylistUpdated
/evo-webroot/hls/playlist.m3u8


hdsMasterPlaylistUpdated
/evo-webroot/hds/stream1.f4m
```

**file** – 更新されたHLSまたはHDSプレイリスト名



### mssPlaylistUpdated, dashPlaylistUpdated

MSS/DASHストリームのプレイリストが更新された際にトリガされるイベント

```
mssPlaylistUpdated
/evo-webroot/mss/stream1/manifest.f4m

dashPlaylistUpdated
/evo-webroot/dash/stream1/manifest.mpd
```

**file** – 更新されたMSS/DASH manifest名



### recordChunkCreated, recordChunkClosed, recordChunkError

新規録画フラグメントのオープン、完了、ディスク上でReady、書き込みエラーしたなどの際にトリガされるイベント

```
/media/record/stream1_part0008.mp4
```

**file** – オープン／クローズ／書き込みエラーがあったrecordフラグメント名



## Web Serverイベント

### streamingSessionStarted

HTTPストリーミングセッションが開始した際に生成されるイベント

- clientIP – 接続しにきたクライエントアドレス

- sessionID – 内部ID

- playlist – プレイリストファイル

- startTime – セッション開始タイム




### streamingSessionEnded

HTTPストリーミングセッションが停止した際に生成されるイベント

- clientIP – 接続クライエントのアドレス

- sessionID – 内部ID

- playlist – プレイリストファイル

- startTime – セッション開始タイム

- stopTime – セッション停止タイム





### fileDownloaded

HTTPファイルダウンロードが完了した際に生成されるイベント

- clientIP – 接続クライエントアドレス

- mediaFile – メディアファイルパス

- startTime – セッション開始タイム

- elapsed – セッション開始からの経過時間(秒)







## APIベースイベント

### cliRequest

EMSがRuntime APIコマンドを受信した

- command – EMSが受信したCLIコマンド

- parameters – CLIコマンドのオプションパラメータ



**例:**

```
command: launchProcess
    parameters:
        fullBinaryPath: d:\demoplay.bat
```



### cliResponse

Runtime APIコマンドに対してEMSが生成するレスポンス

```
data:
        arguments: 
        configId: 1
        fullBinaryPath: d:\demoplay.bat
        keepAlive: true
        operationType: 6
    description: Process enqueued for start
    status: SUCCESS
```

- data – CLIレスポンスについてのオプションデータ

- description – CLIレスポンスについての詳細情報

- status – SUCCESS または FAIL  CLIコマンドのパース結果





### processStarted, processStopped

launchProcess APIコマンドリクエストによりプロセスが開始／停止した

```
arguments: 
configId: 1
    fullBinaryPath: d:\demoplay.bat
    keepAlive: true
    operationType: 6
```

- arguments – 開始プロセスのパラメータ

- configId – 開始プロセスの設定ID

- fullBinaryPath – 開始プロセスのバイナリフルパス

- keepAlive – trueの場合、接続が切断された際、再接続が毎秒試行されます

- operationType – 0:STANDARD, 1:PUSH, 2:PULL, 3:HLS, 4:HDS, 5:RECORD, or 6:LAUNCHPROCESS.




### timerCreated

setTimer APIコマンドで新規タイマーが作成された

```
arguments: 
configId: 1
    fullBinaryPath: d:\demoplay.bat
    keepAlive: true
    operationType: 6
```

- timerId – 新規作成されたタイマーのID

- triggerCount – タイマーが作成されて以降トリガした回数

- value – タイマー値





### timerTriggered

タイマーがトリガされた

```
timerId: 9
triggerCount: 0
value: 100
```

- timerId – トリガされたタイマーID

- triggerCount – タイマーが作成されて以降トリガした回数

- value – タイマー値





### timerClosed

タイマーがクローズされ、以降timerTriggerdイベントは起きません

```
timerId: 9
triggerCount: 2
value: 100
```

- timerId – クローズしたタイマーID

- triggerCount – タイマーが作成されて以降トリガした回数

- value – タイマー値




## 接続ベースのイベント

### protocolRegisteredToApp

接続が確立された

```
    customParameters:
        ip: 127.0.0.1
        port: 1112
        protocol: inboundJsonCli
        sslCert: 
        sslKey: 
        useLengthPadding: true
    protocolType: IJSONCLI
```

- customParameters – プロトコルカスタムパラメータ

- protocolType – プロトコルタイプ




### protocolUnregisteredFromApp

接続が切断された

```
    customParameters:
        ip: 127.0.0.1
        port: 1112
        protocol: inboundJsonCli
        sslCert: 
        sslKey: 
        useLengthPadding: true
    protocolType: IJSONCLI
```

- customParameters – プロトコルカスタムパラメータ

- protocolType – プロトコルタイプ





### carrierCreated

TCPソケットなど、なにかのIOハンドラが作成された





### carrierClosed

UDPソケットなど、なにかのIOハンドラがクローズされた





## アプリケーションベースのイベント

### applicationStart, applicationStop

内部EMSアプリケーションの起動および停止（サーバーシャットダウン等）の直後に生成されるイベント

```
config:
acceptors:
0:
	ip: 127.0.0.1
	port: 1112
	protocol: inboundJsonCli
	sslCert:
	sslKey:
	useLengthPadding: true
1:
	ip: 0.0.0.0
	port: 7777
	protocol: inboundHttpJsonCli
	sslCert:
	sslKey:
2:
	ip: 0.0.0.0
	port: 1935
	protocol: inboundRtmp
	sslCert:
	sslKey:
3:
	clustering: true
	ip: 127.0.0.1
	port: 1936
	protocol: inboundRtmp
	sslCert:
	sslKey:
4:
	clustering: true
	ip: 127.0.0.1
	port: 1113
	protocol: inboundBinVariant
	sslCert:
	sslKey:
5:
	ip: 0.0.0.0
	port: 5544
	protocol: inboundRtsp
	sslCert:
	sslKey:
6:
	ip: 0.0.0.0
	port: 6666
	protocol: inboundLiveFlv
	sslCert:
	sslKey:
	waitForMetadata: true
aliases:
	0: er
	1: live
	2: vod
appDir: C:\emsdemo\config\
authPersistenceFile: ..\config\auth.xml
bandwidthLimitPersistenceFile: ..\config\bandwidthlimits.xml
connectionsLimitPersistenceFile: ..\config\connlimits.xml
default: true
description: EVOSTREAM MEDIA SERVER
eventLogger:
	sinks:
	1:
		filename: ..\logs\events.txt
		format: text
		type: file
		hasStreamAliases: false
		initApplicationFunction: GetApplication_evostreamms
		initFactoryFunction: GetFactory_evostreamms
		library:
		maxRtmpOutBuffer: 524288
		mediaStorage:
			1:
				description: Default media storage
				mediaFolder: ../media
		metaFileGenerator: false
		name: evostreamms
		protocol: dynamiclinklibrary
		pushPullPersistenceFile: ..\config\pushPullSetup.xml
		rtcpDetectionInterval: 15
		streamsExpireTimer: 10
		validateHandshake: false
id: 1
name: evostreamms
```

- config – アプリケーション設定

- id – アプリケーションID

- name – アプリケーション名




### serverStarted

サーバーが起動した

```
00001	serverStarted
	PID: 9180
	banner: EvoStream Media Server (www.evostream.com) version 2.0.0 build 5550 with hash: eab81ed5ed39d3794e77408249f51817142b90ba - QBert - (built for Microsoft Windows 10 Pro-10.0.14393-x86_64 on 2017-10-04T10:12:53.000)
	branchName: release_2.0.0
	buildDate: 2017-10-04T10:12:53.000
	buildNumber: 5550
	codeName: QBert
	hash: eab81ed5ed39d3794e77408249f51817142b90ba
	releaseNumber: 2.0.0
```



### serverStopped

サーバーが停止


```
00002	serverStopping
	PID: 9180
	banner: EvoStream Media Server (www.evostream.com) version 2.0.0 build 5550 with hash: eab81ed5ed39d3794e77408249f51817142b90ba - QBert - (built for Microsoft Windows 10 Pro-10.0.14393-x86_64 on 2017-10-04T10:12:53.000)
	branchName: release_2.0.0
	buildDate: 2017-10-04T10:12:53.000
	buildNumber: 5550
	codeName: QBert
	hash: eab81ed5ed39d3794e77408249f51817142b90ba
	releaseNumber: 2.0.0
```

------

## Notes:

-  config.luaの[eventLogger](userguide_configlua.html#eventLogger)の項がコメントアウトされ、イベント利用が有効化されていることを確認してください


------

## 関連リンク

- [List of Events](eventslist.html)

  ​