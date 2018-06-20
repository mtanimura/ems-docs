---
title: createDASHStream
keywords: api
sidebar: api_sidebar
permalink: createDASHStream.html
folder: api
toc: false
---


H.264/AAC, H.265/AACからDynamic Adaptive Streaming over HTTP (DASH)を生成します。DASHは複数ベンダーに採用され相互運用促進されるようにMoving Picture Experts Group (MPEG)でHTTP adaptive-bitrateストリーミングの標準として開発されました。



## API パラメータ

|    パラメータ名    |  タイプ   |                必須かどうか                 |        デフォルト値        | 説明                              |
| :------------------: | :-----: | :-------: | :--------------------------------------: | ---------------------------------------- |
|   localStreamNames   | 文字列  |   true    |                  *null*                  | 入力につかわれるストリーム。アクティブなストリーム名のカンマ区切りのリストです |
|     targetFolder     | 文字列  |   true    |                  *null*                  | manifestやfragmentファイルの保存フォルダ。DASHクライエントからアクセスできる必要があります。通常はサーバーのweb-rootが指定されます |
|      bandwidths      | 整数値 |   false   |                    0                     | `localStreamNames`リストの各ストリームに割り当てられる帯域。カンマ区切のリストです |
|      groupName       | 文字列  |   false   |        *dash_group_xxxx (random)*        | DASHストリーム／グループに割り当てられる名前。`localStreamNames`パラメータが一つしかエントリが無く、`groupName`の指定が無い場合は、`groupName`は入力ストリーム名となります |
|     playlistType     | 文字列  |   false   |                appending                 | **appending** または**rolling**のどちらかを設定します。Appendingプレイリストは連続的なプレイリストを生成し、rollingプレイリストはplayListLength設定に従います |
|    playlistLength    | 整数値 |   false   |                    10                    | サーバーが旧いfragmentを上書きし始めるまでのfragment数。 `playlistType`が **rolling**設定のときのみ有効でその他では無視されます |
|     manifestName     | 文字列  |   false   |               manifest.mpd               | manifestファイル名 |
|     chunkLength      | ブーリアン |   false   |                    10                    | 各fragmentの長さ(秒)。最小値は1(秒)です |
|      chunkOnIDR      | ブーリアン |   false   |                 1 *true*                 | **true**の場合、chunkingはIDRでのみ実行されます。その他の場合はchunk length毎にchunkingは実行されます |
|      keepAlive       | ブーリアン |   false   |                 1 *true*                 | **true**の場合、EMSは接続が切断した際、ストリームソースとの接続を再構築しようと試行します |
| overwriteDestination | ブーリアン |   false   |                 1 *true*                 | **true**の場合保存先に上書き保存します |
| staleRetentionCount  | ブーリアン |   false   | *指定がなければplaylistLength値となります* | 現在のバージョンのプレイリストにリストされるもの以外に保持される旧いファイル数 **rolling** プレイリストの場合のみ有効 |
|  cleanupDestination  | ブーリアン |   false   |                0 *false*                 | **true**の場合、ターゲットフォルダ上のすべてのmanifestおよびfragmentファイルがHLS生成開始前に削除されます |
|    dynamicProfile    | ブーリアン |   false   |                 *1 true*                 | live DASH向けにはパラメータを**1**(デフォルト値)に設定してください。それ以外はVOD用の**0** に設定してください |





## API Call テンプレート

```
createDASHStream localStreamname=<localStreamName> targetfolder=<webrootFolder> groupname=<groupName>
```



### サンプル API Call

```
createDASHStream localstreamnames=testpullStream targetfolder=/var/evo-webroot groupname=testDASH
```



### JSONのSuccess Response

```
{
"data":{
    "bandwidths":[0],
    "chunkLength":10,
    "chunkOnIDR":true,
    "cleanupDestination":false,
    "configIds":[11],
    "dynamicProfile":true,
    "groupName":"testDASH",
    "keepAlive":true,
    "localStreamNames":["testpullStream"],
    "manifestName":"manifest.mpd",
    "overwriteDestination":true,
    "playlistLength":10,
    "playlistType":"appending",
    "publishingPoint":"",
    "staleRetentionCount":10,
    "targetFolder":"\/var\/evo-webroot"
},
"description":"DASH stream created",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは下記の詳細を含みます:

- data – パースするデータ
  - bandwidths – ストリーミングの帯域を指定する整数値の配列
  - chunkLength – プレイリストエレメント(.mpdファイル)の長さ(秒)
  - chunkOnIDR – **true**の場合、IDR境界でchunkが作成されます
  - cleanupDestination – **true**の場合、DASHファイル生成前にターゲットフォルダ上のDASHファイルは削除されます
  - configIds – コマンドの設定ID
  - dynamicProfile – DASHストリームが**live**か**VOD**か
  - groupName – DASHファイルのターゲットフォルダ名
  - keepAlive–  **true**の場合、接続断の際ストリーム再接続試行されます
  - localStreamNames– ストリームのローカル名の配列
  - manifestName – manifestファイル名。空白の場合、デフォルト値は**manifest**です
  - overwriteDestination –  **true**の場合、DASH生成時に上書き有効
  - playlistLength – サーバーが旧ファイルを上書きするまでのfragment数。rollingプレイリストタイプの場合にのみ有用です
  - playlistType – **appending** または **rolling**
  - staleRetentionCount – 現在のバージョンのプレイリストを除き、古いファイルの保持数。**rolling**プレイリストでのみ有効
  - targetFolder - manifestファイルおよびchunkファイル保存先
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- プレイリストを先頭からスタートしたい場合、`createDASHStream` コマンドを`pullStream`コマンドより先に実行してください
- autoDASH使用時、下記のパラメータは変更されません:
  - keepAlive - 常にfalse
  - cleanupDestination - 常にtrue
  - createMasterPlaylist - 常にfalse
  - overwriteDestination - 常にtrue
  - playlistType - 常に"rolling"

------

## 関連リンク

- [Adding Streams](userguide_add.html#adding-http-streams)
- [Create DASH Stream](userguide_createdash.html)
- [autoHLS](userguide_configlua.html#autodashhlshdsmss)
