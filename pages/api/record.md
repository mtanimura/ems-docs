---
title: record
keywords: api
sidebar: api_sidebar
permalink: record.html
folder: api
toc: false
---



インバウンドストリームの録画を行います。`record`コマンドを使用してユーザがストリームの録画を行うことが可能です（当該ストリームがまだ存在していなくても）。サーバーに新規ストリームが入ってくると、ストリームリストに対して録画すべきかどうか確認が行われます。



## API パラメータ



| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-----------------: | :-----: | :-------: | :-----------: | :--------------------------------------- |
|   localStreamName   | 文字列  |   true    |    *null*     | 録画の入力に使われるストリーム名 |
|     pathToFile      | 文字列  |   true    |    *null*     | 書き出しパスおよびファイル名 |
|        type         | 文字列  |   false   |      mp4      | **TS** か **MP4** もしくは **FLV**             |
|      overwrite      | ブーリアン |   false   |   0 *false*   | **false**の場合、ファイルがすでに存在していた場合には、ファイル名末尾に適切な番号が付け加えられます。 **true**の場合ファイルは上書きされます |
|      keepAlive      | ブーリアン |   false   |   1 *true*    | **true**の場合、サーバーはストリームが得られる度に録画を再開します。|
|     chunkLength     | 整数値 |   false   | 0 *disabled*  | 0意外の場合、recordコマンドは、`chunkLength`で指定した秒数毎に新規録画を開始します。|
|     waitForIDR      | ブーリアン |   false   |   1 *true*    | trueの場合、録画がチャンクファイルを生成する場合に適用され、IDR境界のみで新規ファイル作成が行われます
|     winQtCompat     | ブーリアン |   false   |   0 *false*   | Windows QuickTimeとの互換性を保持するため32ビットヘッダフィールドを強制します |
| dateFolderStructure | ブーリアン |   false   |   0 *false*   | **true**の場合、フォルダ名は **YYYYMMDD** フォーマットで作成されます。録画されたファイルは作成された時刻にもとづいて該当フォルダに保存されます |

## API Call テンプレート

```
record localStreamName=<localStreamName> pathtofile=</recording/path/fileName> type=<ts/MP4/FLV>
```



### サンプル API Call

```
record localStreamName=testpullStream pathtofile=../media/testRecord type=mp4
```



### JSONのSuccess Response

```
{
"data":{
    "chunkLength":0,
    "computedPathToFile":"..\/media\/testRecord.mp4",
    "configId":12,
    "dateFolderStructure":false,
    "hasAudio":true,
    "keepAlive":true,
    "localStreamName":"testpullstream",
    "mp4BinPath":"..\\evo-mp4writer.exe",
    "operationType":7,
    "overwrite":true,
    "pathToFile":"..\/media\/testRecord ",
    "preset":0,
    "type":"mp4",
    "waitForIDR":false,
    "winQtCompat":true
},
"description":"Recording Stream",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - chunkLength - プレイリストエレメントの長さ(秒)
  - computedPathToFile – 録画されるストリームのパスおよびファイル名The path and file name of the recorded stream
  - configID – 設定ID
  - dateFolderStructure – **true**の場合、日付ごとにチャンクファイルは整理されます
  - hasAudio – 録画されるストリームがオーディオ含むかどうか、無しの場合はfalse
  - keepAlive – **true**の場合、接続が切断した際、ストリーム再接続が試行されます
  - localStreamName – ストリームのローカル名
  - mp4BinPath - mp4 writerのパス
  - operationType – オペレーションタイプ、内部使用
  - overwrite – **true**の場合、同名ファイルは上書きされます
  - pathToFile – 録画ファイルが保存されるフォルダパス
  - type – 録画ファイル・タイプ。 \`**flv**\`か\`**ts**\`もしくは ‘**mp4’**
  - waitForIDR – **true**の場合、新規ファイルはIDR境界上のみで作成されます
  - winQtCompat – **true**の場合、Windows QuickTime互換性のため32ビットヘッダフィールドが強制されます
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- 録画ファイルを先頭からストリーム再生開始させたい場合は、recordを`pullStream`より先に発行してください


------

## 関連リンク

- [Record a Stream](userguide_record.html)