---
title: createHDSStream
keywords: api
sidebar: api_sidebar
permalink: createHDSStream.html
folder: api
toc: false
---

H.264/AACからHDS (HTTP Dynamic Streaming) ストリームを生成します。Create an HDS (HTTP Dynamic Streaming) HDSは標準的なMP4メディアをHTTP接続でストリームするのに使用されます。Appleが開発したHLSに対し、HDSはAdobeにより開発された新技術です。



## API パラメータ

|    パラメータ名    |  タイプ   |                必須かどうか                 |        デフォルト値        | 説明                              |
| :------------------: | :-----: | :-------: | :--------------------------------------: | ---------------------------------------- |
|   localStreamNames   | 文字列  |   true    |                  *null*                  | 入力につかわれるストリーム。アクティブなストリーム名のカンマ区切りのリストです |
|     targetFolder     | 文字列  |   true    |                  *null*                  | manifest(.f4m)やfragment(f4v)ファイルの保存フォルダ。HDSクライエントからアクセスできる必要があります。通常はサーバーのweb-rootが指定されます |
|      bandwidths      | 整数値 |   false   |                    0                     | `localStreamNames`リストの各ストリームに割り当てられる帯域。カンマ区切のリストです |
|    chunkBaseName     | 文字列  |   false   |                   f4v                    | fragmentの生成につかわれるbase name デフォルト値は **f4vSeg1-FragXXX**のようなフォーマットになります |
|     chunkLength      | 整数値 |   false   |                    10                    | 作成されるfragmentの長さ(秒)。最小値は**1**(秒)です |
|      chunkOnIDR      | ブーリアン |   false   |                 1 *true*                 | **true**の場合、chunkingはIDRでのみ実行されます。その他の場合はchunk length毎にchunkingは実行されます |
|      groupName       | 文字列  |   false   | *(指定がなければhds_group_xxxx)形式のランダム名となります* | HDSストリーム／グループに割り当てられる名前。`localStreamNames`パラメータが一つしかエントリが無く、`groupName`の指定が無い場合は、`groupName`は入力ストリーム名となります |
|      keepAlive       | ブーリアン |   false   |                 1 *true*                 | **true**の場合、EMSは接続が切断した際、ストリームソースとの接続を再構築しようと試行します |
|     manifestName     | 文字列  |   false   |    *falseの場合デフォルトでストリーム名となります*    | manifestファイル名 |
| overwriteDestination | ブーリアン |   false   |                 1 *true*                 | **true**の場合保存先に上書き保存します |
|     playlistType     | 文字列  |   false   |                appending                 | **appending** または**rolling**のどちらかを設定します。Appendingプレイリストは連続的なプレイリストを生成し、rollingプレイリストはplayListLength設定に従います |
|    playlistLength    | 整数値 |   false   |                    10                    | サーバーが旧いfragmentを上書きし始めるまでのfragment数。 `playlistType`が **rolling**設定のときのみ有効でその他では無視されます |
| staleRetentionCount  | 整数値 |   false   | *指定がなければplaylistLength値となります* | 現在のバージョンのプレイリストにリストされるもの以外に保持される旧いファイル数 **rolling** プレイリストの場合のみ有効 |
| createMasterPlaylist | ブーリアン |   false   |                 1 *true*                 | **true**の場合、マスタープレイリストが生成されます |
|  cleanupDestination  | ブーリアン |   false   |                0 *false*                 | **true**の場合、ターゲットフォルダ上のすべてのmanifestおよびfragmentファイルがHDS生成開始前に削除されます |


## API Call テンプレート

```
createHDSStream localStreamname=<localStreamName> targetfolder=<webrootFolder> groupname=<groupName>
```



### サンプル API Call

```
createHDSStream localstreamnames=testpullStream targetfolder=/var/evo-webroot groupname=testHDS playlisttype=rolling
```



### JSONのSuccess Response

```
{
"data":{
    "bandwidths":[0],
    "chunkBaseName":"f4v",
    "chunkLength":10,
    "chunkOnIDR":true,
    "cleanupDestination":false,
    "configIds":[9],
    "createMasterPlaylist":true,
    "groupName":"testHDS",
    "keepAlive":true,
    "localStreamNames":["testpullStream"],
    "manifestName":"",
    "overwriteDestination":true,
    "playlistLength":10,
    "playlistType":"rolling",
    "staleRetentionCount":10,
    "targetFolder":"\/var\/evo-webroot",
},
"description":"HDS stream created",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは下記の詳細を含みます:

- data – パースするデータ
  - bandwidths – ストリーミングの帯域を指定する整数値の配列
  - chunkBaseName – 出力HDS chunksのベース名またはプレフィックス
  - chunkLength – プレイリストエレメント(.f4mファイル)の長さ(秒)
  - chunkOnIDR – **true**の場合、IDR境界でchunkが作成されます
  - cleanupDestination – **true**の場合、HDSファイル生成前にターゲットフォルダ上のHDSファイルは削除されます
  - configIds – コマンドの設定ID
  - createMasterPlaylist – **true**の場合、マスタープレイリストが生成されます

  - groupName – HDSファイルのターゲットフォルダ名
  - keepAlive–  **true**の場合、接続断の際ストリーム再接続試行されます
  - localStreamNames– ストリームのローカル名の配列
  - manifestName – manifest(.f4m)ファイル名。空白の場合、デフォルト値は**manifest**です
  - overwriteDestination –  **true**の場合、HDS生成時に上書き有効
  - playlistLength – サーバーが旧ファイルを上書きするまでのfragment数。rollingプレイリストタイプの場合にのみ有用です
  - playlistType – **appending** または **rolling**
  - staleRetentionCount – 現在のバージョンのプレイリストを除き、古いファイルの保持数。**rolling**プレイリストでのみ有効
  - targetFolder - manifestファイルおよびchunkファイル保存先
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------
## Notes

- プレイリストを先頭からスタートしたい場合、`createHDSStream` コマンドを`pullStream`コマンドより先に実行してください
- autoHDS使用時、下記のパラメータは変更されません:
  - keepAlive - 常にfalse
  - cleanupDestination - 常にtrue
  - createMasterPlaylist - 常にfalse
  - overwriteDestination - 常にtrue
  - playlistType - 常に"rolling"

------

## 関連リンク

- [Adding Streams](userguide_add.html#adding-http-streams)
- [Create HDS Stream](userguide_createhds.html)
- [autoHDS](userguide_configlua.html#autodashhlshdsmss)
