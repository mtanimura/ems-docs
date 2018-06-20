---
title: createHLSStream
keywords: api
sidebar: api_sidebar
permalink: createHLSStream.html
folder: api
toc: false
---

H.264/AAC, H.265/AACストリームからHTTP Live Stream (HLS)を生成します。HLSはiPhoneやiPadなどのiOSデバイス向けのライブフィードのストリーミングに使用されます



## API パラメータ

|    パラメータ名    |  タイプ   |                必須かどうか                 |        デフォルト値        | 説明                              |
| :------------------: | :-----: | :-------: | :--------------------------------------: | ---------------------------------------- |
|   localStreamNames   | 文字列  |   true    |                  *null*                  | 入力にしようされるストリーム。コンマで区切られたアクティブストリーム名（local stream name） |
|     targetFolder     | 文字列  |   true    |                  *null*                  | すべての *.ts/*.m3u8 ファイルが保存されるフォルダ。HLSクライエントにアクセス可である必要があります。通常サーバーのweb-rootに設定されます |
|      keepAlive       | ブーリアン |   false   |                 1 *true*                 | **true**の場合、EMSは接続が切断した際、ストリームソースとの接続を再構築しようと試行します。 |
| overwriteDestination | ブーリアン |   false   |                 1 *true*                 | **true**の場合保存先に上書き保存します |
| staleRetentionCount  | 整数値 |   false   | *指定がなければplaylistLengthの設定値を使用します* | 現在のバージョンのプレイリストにリストされるもの以外に保持される旧いファイル数 **rolling** プレイリストの場合のみ有効 |
| createMasterPlaylist | ブーリアン |   false   |                 1 *true*                 | **true**の場合、マスタープレイリストが生成されます |
|  cleanupDestination  | ブーリアン |   false   |                0 *false*                 | **true**の場合、ターゲットフォルダ上のすべての.tsファイルおよび.m3u8ファイルがHLS生成開始前に削除されます |
|      bandwidths      | 整数値 |   false   |                    0                     | `localStreamNames`リスト上の各ストリームへの帯域。コンマで区切られたリストを使用可 |
|      groupName       | 文字列  |   false   | *hls_group_xxxxのようにランダムな名前が付けられます* | HLSストリームやグループに割り当てられるグループ名。`localStreamNames`パラメータに`groupName`の指定がなければ、`groupName`には入力ストリーム名が適用されます |
|     playlistType     | 文字列  |   false   |                appending                 | **appending** または**rolling**を設定可。Appendingプレイリストはプレイリストを連続的に生成します。rollingプレイリストはplayListLength設定に依存します |
|    playlistLength    | 整数値 |   false   |                    10                    | サーバーが旧いfragmentを上書きしはじめるまでのfragment数設定。`playlistType`のパラメータが **rolling**に設定されている際のみ有効 |
|     playlistName     | 文字列  |   false   |              playlist.m3u8               | プレイリスト(.m3u8)のファイル名 |
|     chunkLength      | 整数値 |   false   |                    10                    | 各プレイリストelement(.ts file)の長さ(秒) 最小値は1(秒) |
|    maxChunkLength    | 整数値 |   false   |                    0                     | 最大許容チャンク長(秒)を指定するパラメータ。主にEMSが次のキーフレームを待つ`chunkOnIDR=true`の場合に意味があります。`maxChunkLength`が`chunkLength`以下の場合、本パラメータは無視されます |
|    chunkBaseName     | 文字列  |   false   |                 segment                  | .tsチャンク生成に使用されるbase name |
|      chunkOnIDR      | ブーリアン |   false   |                 1 *true*                 | **true**の場合 chunkingはIDRでのみ実行されます。chunkingはchunk lengthに到達する度に実行されます |
|       drmType        | 文字列  |   false   |                   none                   | DRM暗号化タイプ設定。設定可能なオプションは **none** (暗号化なし), **evo** (AES Encryption),**SAMPLE-AES** (Sample-AES), **verimatrix**(Verimatrix DRM)です。Verimatrix DRMの場合、config.luaファイルの“drm” セクションがアクティブかつ適切に設定されている必要があります |
|     AESKeyCount      | 整数値 |   false   |                    5                     | HLSストリームを暗号化する際、自動生成・ローテーションされるkey数 |
|      audioOnly       | ブーリアン |   false   |                0 *false*                 | 生成されるストリームがオーディオのみとなるように指定。1(true)に設定されるとストリームはビデオは含まれません |
|      hlsResume       | ブーリアン |   false   |                0 *false*                 | **true**の場合、EMSシャットダウンやストリームソースの接続断があった場合もHLSは前につくられた子プレイリストにappendし再開されます。 |
|    cleanupOnClose    | ブーリアン |   false   |                0 *false*                 | **true**の場合、ストリームが削除されるか、シャットダウン、接続断された場合に当該ストリームに紐付いたHLSファイルが削除されます |
|     useByteRange     | ブーリアン |   false   |                0 *false*                 | **true**の場合、HLSのEXT-X-BYTERANGE機能が使用されます(ver4以降) |
|      fileLength      | 整数値 |   false   |                0 *false*                 | `useByteRange=1`の場合にはこのパラメータも設定する必要があります。チャンクファイルサイズ設定で、EXT-X-BYTERANGEの際に`chunkLength`を置き換えます。|
|    useSystemTime     | ブーリアン |   false   |                0 *false*                 | **true**の場合、プレイリストのタイムスタンプにUTCが適用されます、その他はローカルサーバータイムが適用されます |
|      offsetTime      | 整数値 |   false   |                    0                     | ビデオを再生開始するオフセット値(秒) |
|     startOffset      | 整数値 |   false   |                    0                     | HLS v6以降で有効なパラメータ。プレイリスト再生のスタートオフセット値(秒)  |





## API Call テンプレート

```
createHLSStream localStreamname=<localStreamName> targetfolder=<webrootFolder> groupname=<groupName>
```



### サンプル API Call

```
createHLSStream localstreamnames=testpullStream targetfolder=/var/evo-webroot groupname=testHLS playlisttype=rolling
```



### JSONのSuccess Response

```
{
"data":{
    "AESKeyCount":5,
    "audioOnly":false,
    "bandwidths":[128],
    "chunkBaseName":"segment",
    "chunkLength":10,
    "chunkOnIDR":true,
    "cleanupDestination":false,
    "cleanupOnClose":false,
    "configIds":[7],
    "createMasterPlaylist":true,
    "drmType":"none",
    "fileLength":0,
    "groupName":"testHLS",
    "hlsResume":false,
    "hlsVersion":6,
    "keepAlive":true,
    "localStreamNames":["testpullStream"],
    "maxChunkLength":0,
    "offsetTime":0,
    "overwriteDestination":true,
    "playlistLength":10,
    "playlistName":"playlist.m3u8",
    "playlistType":"rolling",
    "publishingPoint":"",
    "staleRetentionCount":10,
    "startOffset":0,
    "targetFolder":"\/var\/evo-webroot",
    "useByteRange":false,
    "useSystemTime":false
},
"description":"HLS stream created",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは下記の詳細を含みます:

- data – パースするデータ
  - AESKeyCount - HLSストリームを暗号化しながら自動的に生成されローテーションされるキー数
  - audioOnly - trueの場合、EMSはオーディオのみストリームします
  - bandwidths – ストリーミングの帯域を指定する整数値の配列
  - chunkBaseName– 出力HLSチャンク名に使用するbase nameまたはprefix
  - chunkLength – プレイリストエレメント(.tsファイル)の長さ(秒)
  - chunkOnIDR – **true**の場合、IDR境界でchunkが作成されます
  - cleanupDestination – **true**の場合、HLSファイル生成前にターゲットフォルダ上のHLSファイルは削除されます
  - cleanupOnClose - **true**の場合、ストリームが接続断となったとき関連するhlsファイルは削除されます
  - configIDs – コマンドの設定ID
  - createMasterPlaylist–**true**の場合、マスタープレイリストが生成されます
  - drmType - DRM暗号化のタイプ
  - fileLength - chunkingのファイルサイズ。**EXT-X-BYTERANGE**の場合に`chunkLength`を置き換えます
  - groupName –  HLSファイルのターゲットフォルダ名
  - hlsResume – **true**の場合、EMSのシャットダウンやソースストリーム接続断があっても、前回の子プレイリストにセグメントappendで再開されます。
  - hlsVersion – HLSバージョン
  - keepAlive–  **true**の場合、接続断の際ストリーム再接続試行されます
  - localStreamNames– ストリームのローカル名の配列
  - maxChunkLength - シングルchunkの最大長
  - offsetTime - ビデオ再生開始オフセット
  - overwriteDestination –  **true**の場合、HLS生成時に上書き有効
  - playlistLength – プレイリストのエレメント数。rollingプレイリストタイプの場合にのみ有用です
  - playlistName– プレイリスト(*.m3u8)のファイル名
  - playlistType – **appending** または **rolling**
  - staleRetentionCount – 現在のバージョンのプレイリストを除き、古いファイルの保持数。**rolling**プレイリストでのみ有効
  - startOffset - プレイリストの再生時のスタートオフセット
  - targetFolder–.ts /.m3u8ファイル保存先
  - useByteRange - HLS (version 4以降)の**EXT-X-BYTERANGE**機能を有効化
  - useSystemTime - プレイリストで使用されるタイムスタンプ
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- EMS起動前に**HLS version**がconfig.luaで適切に設定されていることを確認してください
- プレイリストを先頭からスタートしたい場合、`createHLSStream`を`pullStream`コマンドより先に実行してください。
- autoHLS使用時、下記のパラメータは変更されません。
  - keepAlive - 常にfalse
  - cleanupDestination - 常にtrue
  - createMasterPlaylist - 常にfalse
  - overwriteDestination - 常にtrue
  - playlistType - 常に"rolling"

------
## 関連リンク

- [hlsVersion](userguide_configlua.html#hlsversion)
- [Adding Streams](userguide_add.html#adding-http-streams)
- [Create HLS Stream](userguide_createhls.html)
- [autoHLS](userguide_configlua.html#autodashhlshdsmss)
