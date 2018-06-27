---
title: launchProcess
keywords: api
sidebar: api_sidebar
permalink: launchProcess.html
folder: api
toc: false
---

ローカルマシン上で外部プロセスの起動を許可します。LibAVConvやFFMPEGなどのアプリケーションと組み合わせてトランスコードする際に使用されます。



## API パラメータ


| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :--------------: | :-----: | :-------: | :--------------------------------------: | ---------------------------------------- |
|  fullBinaryPath  | 文字列  |   true    |                  *null*                  | 実行可能バイナリへのパス |
|    keepAlive     | ブーリアン |   false   |                 1 *true*                 | `keepAlive`が１の場合、何らかの理由でプロセスが落ちた場合にEMSは再起動を試みます |
|    arguments     | 文字列  |   false   |           *zero-length string*           | プロセスにわたすべき引数リスト。エスケープされた空白(“\ “) 文字で区切られます |
|    groupName     | 文字列  |   false   | *割当がない場合, ランダムな値のprocess_group_xxxが割当られます* | プロセスに割り当てるグループ名 |
|  $[ENV]=[VALUE]  | 文字列  |   false   |           *zero-length string*           | プロセス起動前に設定が必要な環境変数 |
| processKillTimer | 整数値 |   false   |                    0                     | processKillTimer(秒)経過後もプロセスが実行中の場合はkillします |



## API Call テンプレート

```
launchProcess parameterA=<value> parameterB=<value> ...
```



### サンプル API Call

```
launchProcess fullBinaryPath=/home/ems/ffmpeg_preset.sh arguments=10fps\ Stream1\ Stream1_10fps keepAlive=1 $SAMPLE_E_VAR=MyVal
```

このサンプルはffmpeg_prest.shスクリプトを起動します。FFMPEGを特定のパラメータ付きで起動するシェルスクリプトです

ffmpeg_preset.shスクリプトへの引数には(“10fps”, “Stream1”, “Stream1_10fps”)と３つの値が例として含まれています。この例ではStream1を10fpsにトランスコードし“Stream1_10fps”というストリーム名として出力するものです。

最後に付加されているパラメータは環境変数(SAMPLE_E_VAR を MyValに設定) 設定例です。



### JSONのSuccess Response

```
{
   "data":{
      "$SAMPLE_E_VAR":"MyVal",
      "arguments":"10fps\ Stream1\ Stream1_10fps",
      "configId":1,
      "fullBinaryPath":"/home/ems/ffmpeg_preset.sh",
      "groupName":"process_group_UHBqMT6C",
      "keepAlive":true,
      "operationType":6
      "processKillTimer":0
   },
   "description":"Process enqueued for start",
   "status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - $[ENV]=[VALUE] – プロセス起動前に設定が必要な環境変数
  - arguments – プロセスに渡されるべき引数のリスト
  - configID – コマンドのconfig ID
  - fullBinaryPath – 起動されたバイナリのフルパス
  - groupName - プロセスに割り当てられたグループ名
  - keepAlive – `keepAlive`が１に設定されている場合、サーバーはexitしたプロセスを再起動します
  - operationType – オペレーションタイプ
  - processKillTimer – processKillTimer(秒)後もプロセスの実行が続く場合はプロセスをkillします
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- If process has processKillTimer and keepAlive of true, the process will be called again after it was killed by the processKillTimer because of the keepAlive mechanism