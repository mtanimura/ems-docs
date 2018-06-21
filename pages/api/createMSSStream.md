---
title: createMSSStream
keywords: api
sidebar: api_sidebar
permalink: createMSSStream.html
folder: api
toc: false
---



H.264/AACからMicrosoft Smooth Stream (MSS) を生成します。MSSは Microsoftにより開発されたストリーミング技術です



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------------: | :-----: | :-------: | :--------------------------------------: | ---------------------------------------- |
|   localStreamNames   | 文字列  |   true    |                  *null*                  | 入力につかわれるストリーム。アクティブなストリーム名のカンマ区切りのリストです |
|     targetFolder     | 文字列  |   true    |                  *null*                  | manifestやfragmentファイルの保存フォルダ。MSSクライエントからアクセスできる必要があります。通常はサーバーのweb-rootが指定されます |
|      bandwidths      | 整数値 |   false   |                    0                     | `localStreamNames`リストの各ストリームに割り当てられる帯域。カンマ区切のリストです |
|      groupName       | 文字列  |   false   |        *mss_group_xxxx (random)*         | MSSストリーム／グループに割り当てられる名前。`localStreamNames`パラメータが一つしかエントリが無く、`groupName`の指定が無い場合は、`groupName`は入力ストリーム名となります |
|     playlistType     | 文字列  |   false   |                Appending                 | **appending** または**rolling**のどちらかを設定します。Appendingプレイリストは連続的なプレイリストを生成し、rollingプレイリストはplayListLength設定に従います |
|    playlistLength    | 整数値 |   false   |                    10                    | サーバーが旧いfragmentを上書きし始めるまでのfragment数。 `playlistType`が **rolling**設定のときのみ有効でその他では無視されます |
|     manifestName     | 文字列  |   false   |              manifest.ismc               | manifestファイル名 |
|     chunkLength      | 整数値 |   false   |                    10                    | 作成されるfragmentの長さ(秒)。最小値は**1**(秒)です |
|      chunkOnIDR      | ブーリアン |   false   |                0 *false*                 | **true**の場合、chunkingはIDRでのみ実行されます。その他の場合はchunk length毎にchunkingは実行されます |
|      keepAlive       | ブーリアン |   false   |                 1 *true*                 | **true**の場合、EMSは接続が切断した際、ストリームソースとの接続を再構築しようと試行します |
| overwriteDestination | ブーリアン |   false   |                 1 *true*                 | **true**の場合保存先に上書き保存します |
| staleRetentionCount  | 整数値 |   false   | *指定がなければplaylistLength値となります* | 現在のバージョンのプレイリストにリストされるもの以外に保持される旧いファイル数 **rolling** プレイリストの場合のみ有効 |
|  cleanupDestination  | ブーリアン |   false   |                0 *false*                 | **true**の場合、ターゲットフォルダ上のすべてのmanifestおよびfragmentファイルがMSS生成開始前に削除されます |
|       ismType        | 文字列  |   false   |                   ismc                   | クライエントにコンテンツを配信する**ismc** か、またはコンテンツをsmooth serverに配信する **isml**  |
|        isLive        | ブーリアン |   false   |                 1 *true*                 | **true**の場合ライブMSSストリームを生成します それ以外は**VOD**用に**0**に設定してください |
|   publishingPoint    | 文字列  |   false   |                  *none*                  | `ismType=isml`の場合に必要なパラメータです。mssコンテンツがインジェストされるREST URIです |
|      ingestMode      | 文字列  |   false   |                  single                  | 非ループインジェストの場合は**single** ローピングインジェストの場合は**loop** |



## API Call テンプレート

```
createMSSStream localStreamname=<localStreamName> targetfolder=<webrootFolder> groupname=<groupName>
```



### サンプル API Call

```
createMSSStream localstreamnames=testpullStream targetfolder=/var/evo-webroot groupname=testMSS playlisttype=rolling
```



### JSONのSuccess Response

```
{
"data":{
    "bandwidths":[0],
    "chunkLength":10,
    "chunkOnIDR":true,
    "cleanupDestination":false,
    "configIds":[10],
    "groupName":"mss",
    "ingestMode":"single",
    “isLive”:”true”,
    "ismType":"ismc",
    "keepAlive":true,
    "localStreamNames":["testpullStream"],
    "manifestName":"manifest.ismc",
    "overwriteDestination":true,
    "playlistLength":10,
    "playlistType":"appending",
    "publishingPoint":"http://192.168.2.35:88/liveingest.isml",
    "staleRetentionCount":10,
    "targetFolder":"\/var\/evo-webroot"
},
"description":"MSS stream created",
"status":"SUCCESS"
}
```



#### JSON Response


JSON responseは以下を含みます:

- data – パースすべきデータ
  - bandwidths – ストリーミングの帯域を指定する整数値の配列
  - chunkLength – プレイリストエレメント(.ismcファイル)の長さ(秒)
  - chunkOnIDR – **true**の場合、IDR境界でchunkが作成されます
  - cleanupDestination – **true**の場合、MSSファイル生成前にターゲットフォルダ上のDASHファイルは削除されます
  - configIds – コマンドの設定ID
  - groupName – MSSファイルのターゲットフォルダ名
  - ingestMode – インジェストタイプ
  - isLive - ライブMSSストリームを生成します、それ以外はVODように**0**に設定
  - keepAlive–  **true**の場合、接続断の際ストリーム再接続試行されます
  - localStreamNames– ストリームのローカル名の配列
  - manifestName – manifestファイル名。空白の場合、デフォルト値は**manifest**です
  - overwriteDestination –  **true**の場合、MSS生成時に上書き有効
  - playlistLength – サーバーが旧ファイルを上書きするまでのfragment数。rollingプレイリストタイプの場合にのみ有用です
  - playlistType – **appending** または **rolling**
  - publishingPoint - mssコンテンツがインジェストされるREST URI
  - staleRetentionCount – 現在のバージョンのプレイリストを除き、古いファイルの保持数。**rolling**プレイリストでのみ有効
  - targetFolder - manifestファイルおよびchunkファイル保存先
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- プレイリストを先頭からスタートしたい場合、`createMSSStream` コマンドを`pullStream`コマンドより先に実行してください
- autoMSS使用時、下記のパラメータは変更されません:
  - keepAlive - 常にfalse
  - cleanupDestination - 常にtrue
  - createMasterPlaylist - 常にfalse
  - overwriteDestination - 常にtrue
  - playlistType - 常に"rolling"

------

## 関連リンク

- [Adding Streams](userguide_add.html#adding-http-streams)
- [Create MSS Stream](userguide_createmss.html)
- [autoMSS](userguide_configlua.html#autodashhlshdsmss)
