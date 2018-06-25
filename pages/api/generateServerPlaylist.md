---
title: generateServerPlaylist
keywords: api
sidebar: api_sidebar
permalink: generateServerPlaylist.html
folder: api
toc: false
---

指定されたソースのサーバーサイドプレイリストを作成します



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :-----: | :-------: | :------------------: | ---------------------------------------- |
|    sources     | 文字列  |   true    |        *null*        | 入力ソースのストリームまたはメディアファイル。ストリーム名またはメディアファイル名のカンマ区切リストです |
|   pathToFile   | 文字列  |   true    |        *null*        | 出力するサーバープレイリストファイルのパス |
| sourceOffsets  | 整数値 |   false   | *zero-length string* | ソースのストリーム／ファイルのオフセット値。カンマ区切りリスト |
|   durations    | 整数値 |   false   | *zero-length string* | ソースのストリーム／ファイルの継続時間値。カンマ区切りリスト |
|     repeat     | ブーリアン |   false   |      0 *false*       | **enabled**の場合、プレイリストの先頭から再生を繰り返します |



## API Call テンプレート

```
generateServerPlaylist sources=<sourceA,sourceB..> pathToFile=<filePathtoSave/fileName.lst> sourceOffsets=<valueA,valueB..> durations=-<valueA,valueB..>
```



### サンプル API Call

```
generateServerPlaylist sources=File1.mp4,File2.mp4 pathToFile=../media/testPlaylist.lst sourceOffsets=0,0 durations=60,1
```



### JSONのSuccess Response

```
{
"data":{
    "durations":[60.1],
    "pathToFile":"..\/media\/testPlaylist.lst",
    "repeat":"0",
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
  - durations – ストリーム／ファイルの継続時間()秒リストのアレイ
  - pathToFile – プレイリストファイルのフルパスおよびファイル名
  - repeat - **enabled**の場合、プレイリストの先頭から再生を繰り返します
  - sourceOffsets – ストリーム／ファイルのオフセット値アレイ
  - sources – ストリームまたはメディアファイルのアレイ


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## Notes

- ソースにはライブストリームまたはmp4ファイルを指定できます

- **sourceOffsets** は各ストリーム／ファイルの開始点を(秒で)指定します。このパラメータはストリームがライブかメディアファイルかを示すのに使用可能です

  - -2 はEMSがライブストリームを検索にいきます。ライブストリームが見つからない場合はソース名のメディアファイル再生を試みます。メディアファイルが見つからない場合、ライブストリームがくるのを待ちます。
  - -1 はソースがライブストリームであることを期待しており、ライブストリームが見つからない場合に*duration*が-1設定の場合EMSはライブストリームを待ち続けます。*duration*がそれ以外の値の場合はEMSは*duration*秒間待って、プレイリストの次の項目に移ります
  - 0 または正の値では、ソースがメディアファイルであることを期待します。EMSはファイルの先頭から*sourceOffset*値のところから再生開始します。ファイルが見つからない場合はプレイリストの次項目にスキップします。
  - -1,-2以外の負の値の場合は、-2と同様となります

- **durations** ソースの再生時間を秒指定します

  - 正の値の場合、EMSがソースストリーム／ファイルを*duration*秒間かまたはストリーム／ファイルの終わりまでの早い方を再生します
  - 0の場合、ストリーム／ファイルは１フレームのみ再生されます
  - 1の場合、EMSはライブストリームがなくなるまで、またはメディアファイルの終わりまで再生します
  - -2の場合、メディアファイルは最後まで再生( -1の場合と同じ)し、ライブソースはストリームが得られなくなるまで再生し、ソースストリームがロストしたらプレイリストの次の項目に進みます。
  - -1,-2以外の負の値の場合は、-2と同様となります


------

## 関連リンク

- [insertPlaylistItem](insertPlaylistItem.html)