---
title: insertPlaylistItem
keywords: api
sidebar: api_sidebar
permalink: insertPlaylistItem.html
folder: api
toc: false
---

RTMPプレイリストに新規項目を挿入します。`insertPlaylistItem`はアクティブな再生中のプレイリストに対してコール可能です。



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|    playllistName     | 文字列 |   true    |    *null*     | ストリームが挿入される*.lstファイル名 |
|   localStreamName    | 文字列 |   true    |    *null*     | 挿入されるライブストリーム名・ファイル名。ファイルの場合パスはmediaStorageの場所からの相対パスである必要があります |
|     insertPoint      | 整数値 |   false   |     -1000     | 挿入されるプレイリストタイムライン上の絶対値ミリ秒。負の値は“immediate”を意味し、次フレームから挿入されます |
|     sourceOffset     | 整数値 |   false   |     -2000     | 開始点(ミリ秒)を指定します。このパラメータはストリームがライブかファイルかを示すために使用できます。**-2000**は`localStreamName`のライブストリームを検索し、ライブストリームが見つからない場合、`localStreamName`という名のメディアファイルを再生試行します。メディアファイルが見つからない場合はライブストリームが得られるまで待ちます。**-1000**は`localStreamName`が明確にライブストリームであることを意味し、durationが**-1**の場合EMSはライブストリームを待ち続けます。durationがそれ以外の場合は設定値秒数待った後プレイリストの次項目に進みます。**0**または**正の値**の場合は`localStreamName`がメディアファイルであることを意味します。ファイルの先頭から`sourceOffset`ミリ秒オフセットで再生を開始します。ファイルが見つからない場合はプレイリスト項目はスキップされます。その他**-1000** および -**2000** 以外の負の値は**-2000**と同義です |
|       duration       | 整数値 |   false   |     -1000     | ストリームの継続時間(ミリ秒) **-1000** はライブストリーム・メディアファイルの終わりまで再生します。**0**は１フレームのみ再生。**正の値** はEMSがストリームをdurationミリ秒間か、ライブストリーム／メディアファイルの終了のどちらか早い方の終わりまで再生。**-1000**以外の**負の値**は**-1000**と同義です
| playlistInstanceName | 文字列 |   false   |    *null*     | `<UUID>;*<playlistFileName>`でフォーマットされたプレイリストインスタンスを特定するのに使用されます。null以外では`localStreamName`を指定したplaylistInstanceNameに、さもなくばすべてのストリーミングプレイリストに`localStreamName`を挿入します |



## API Call テンプレート

```
insertPlaylistItem playlistName=<testPlaylist.lst> localStreamName=<localStreamName> insertPoint=<value> sourceOffset=<value> duration=<value>
```



### サンプル API Call

```
insertPlaylistItem playlistName=bunny.lst localStreamName=testpullStream insertPoint=-1000 sourceOffset=0 duration=10
```



### JSONのSuccess Response

```
{
"data":{
    "durations":[60.1],
    "pathToFile":"..\/media\/testPlaylist.lst",
    "sourceOffsets":[0,0],
    "sources":["FileA.mp4","FileB.mp4"]
},
"description":"Server playlist written to ..\/media\/testPlaylist.lst",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - duration – リストの各ストリーム／ファイルの継続時間(秒)アレイ
  - insertPoint - 挿入されるプレイリストタイムライン上の絶対ミリ秒値
  - localStreamName – 挿入ライブストリーム／ファイル名
  - playlistName - ストリームが挿入される*.lstファイル名
  - sourceOffsets – リストの各ストリーム／ファイルのオフセット値のアレイ


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- この関数はプレイリストファイルそのものを変更しせず、メモリ上のファイルを変更するのみです

- `sourceOffset`およびdurationパラメータはプレイリストファイルの作成と同様の動作ですが、秒単位ではなく**ミリ秒**単位で動作します


------

## 関連リンク

- [generateServerPlaylist](generateServerPlaylist.html)