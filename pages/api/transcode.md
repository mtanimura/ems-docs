---
title: transcode
keywords: api
sidebar: api_sidebar
permalink: transcode.html
folder: api
toc: false
---



ビデオ／オーディオストリームの圧縮性質を変更します。ソースストリームから解像度やビットレート変更したり、VP8やMPEG2ストリームをH.264ストリームに変更したりすることができます。またオーバーレイを入れたりクロップすることも可能です。


**トランスコードには多大なコンピュータリソースを必要とし性能へのインパクトが大きいです。一般的なガイドラインとしては、ひとつのHDストリームのトランスコードジョブに対して１CPUコアが必要となります**



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-------------------------: | :-----: | :-----------: | :------------------------------: | ---------------------------------------- |
|           source            | 文字列  |     true      |              *null*              | URIかまたはEMSからのローカルストリーム名を使用可 |
|        destinations         | 文字列  |     true      |              *null*              | トランスコード処理したストリームのターゲットURIまたはストリーム名。名前のみ与えた場合EMSにプッシュバックされます |
|      targetStreamNames      | 文字列  |     false     |  transcoded_xxxx *(timestamp)*   | 保存先でのストリーム名。指定がない場合はフルURIが保存先に使用され、タイムスタンプ値が名前に使用されます
|          groupName          | 文字列  |     false     | transcoded_group_xxxx *(random)* | グループ名。指定がない場合ランダムな値が`groupName`に適用されます |
|        videoBitrates        | 整数値 |     false     |      入力ビデオビットレート       | 出力ビデオターゲットビットレート(bit/s, kbit/s) 入力ビットレートをコピーするには`**copy**`を使用可能です。空の値はビデオ無しを意味します |
|         videoSizes          | 整数値 |     false     |        入力ビデオサイズ        | 出力ビデオターゲットサイズ (width x height) 例: 240x480 *下記Note 3参照* |
| videoAdvancedParamsProfiles | 文字列  |     false     |              *null*              | 適用ビデオプロファイルテンプレート名。'evo-avconv-presets'フォルダのサンプルプリセットを参照してください *下記Note 3参照* |
|        audioBitrates        | 整数値 |     false     |      入力オーディオビットレート       | 出力オーディオターゲットビットレート(bit/s, kbit/s) 入力ビットレートをコピーするには`**copy**`を使用可能です。空の値はオーディオ無しを意味します |
|     audioChannelsCounts     | 整数値 |     false     |   入力オーディオチャンネル数    | 出力オーディオターゲットチャンネル数。使用可能な数値は**1** (モノラル)、 **2** (ステレオ)などで、入力のオーディオチャンネル数にも依存します*下記Note 4参照* |
|      audioFrequencies       | 文字列  |     false     |     入力オーディオ周波数      | 出力オーディオターゲット周波数 (`Hz`まはた`kHz`*下記Note 4参照* |
| audioAdvancedParamsProfiles | 文字列  |     false     |              *null*              | オーディオプロファイルテンプレート名 *下記Note 4参照* |
|          overlays           | 文字列  |     false     |              *null*              | オーバーレイの場所。(通常PNGフォーマットの)ビデオ解像度より小さなサイズのアルファ付き静止画ファイル。画面左上から配置されます |
|          croppings          | 文字列  |     false     |              *null*              | クロップの位置とサイズ 'left : top : width : height' フォーマット (例 0:0:200:100 位置はオプショナルで200:100の場合は中央に200 x 100ピクセルで配置されます。使用可能な数値はビデオ解像度以内までに制限されます |
|          keepAlive          | 整数値 |     false     |             1 *true*             | **true**の場合、アクティベートされたトランスコードは再開されます |
|        commandFlags         | 整数値 |     false     |              *null*              | ベースラインtranscodeコマンドでサポートｓれていないトランスコードプロセスへのコマンド |

## API Call テンプレート

```
transcode source=<sourceURL> groupName=<groupName> destinations=<destinationStreamName> anyTranscodeParameter=<parameterValue>
```



### サンプル API Call

```
transcode source=rtmp://s2pchzxmtymn2k.cloudfront.net/cfx/st/mp4:sintel.mp4 groupName=testGroup destinations=testTranscode groupName=group videoBitrates=200k audioBitrates=copy
```



### JSONのSuccess Response

```
{
"data":{
    "audioAdvancedParamsProfiles":["na"],
    "audioBitrates":["copy"],
    "audioChannelsCounts":["na"],
    "audioFrequencies":["na"],
    "croppings":["na"],
    "destinations":["stream1"],
    "dstUriPrefix":"-f flv tcp:\/\/localhost:6666\/",
    "emsTargetStreamName":"stream1",
    "fullBinaryPath":"C:\\EvoStream\\emsTranscoder.bat",
    "groupName":"group",
    "keepAlive":true,
    "localStreamName":"",
    "overlays":["na"],
    "source":"rtmp:\/\/s2pchzxmtymn2k.cloudfront.net\/cfx\/st\/mp4:sintel.mp4",
    "srcUriPrefix":"rtsp:\/\/localhost:5544\/",
    "targetStreamNames":["testTranscode"],
    "videoAdvancedParamsProfiles":["na"],
    "videoBitrates":["200k"],
    "videoSizes":["na"]
},
"description":"Transcoding successfully started.",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - audioAdvancedParamsProfiles - オーディオに使用されるプロファイルプリセット名を指定する文字列アレイ
  - audioBitrates - 出力オーディオターゲットビットレートの整数値アレイ
  - audioChannelsCounts - オーディオチャンネル数設定値のアレイ
  - croppings - クロップの位置とサイズの設定値のアレイ
  - destinations - ターゲットURIまたはストリーム名のアレイ
  - dstUriPrefix - 保存先がストリーム名の場合のデフォルト保存先
  - emsTargetStreamName - EMSが内部使用するターゲットストリーム名
  - fullBinaryPath - トランスコードバイナリの場所
  - groupName - トランスコードプロセスに紐付けられるグループ名
  - keepAlive - アクティベートされていればトランスコードは再開します
  - localStreamName - ソースEMSストリーム名
  - overlays - オーバーレイに使用される静止画ファイルの場所
  - source - トランスコードへの入力に使用されるストリーム／ファイル
  - srcUriPrefix - ソースがストリーム名の場合のデフォルトソース
  - targetStreamNames - 保存先で使用されるストリーム名のアレイ
  - videoAdvancedParamsProfiles - ビデオプロファイルプリセット名を指定する文字列アレイ
  - videoBitrates - 出力ビデオターゲットビットレート値のアレイ
  - videoSizes - ビデオサイズターゲット値アレイ
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- 複数形のパラメータでは単数・複数の設定値が使用可能です

  複数の値はカンマ区切りとしてください。複数の値を設定すると複数の新規ストリームが生成されます

- 複数のパラメータには同数の設定値が必要です

  **順番が重要です!** 最初の設定値が最初のストリームに、２番目の設定値が２番めのストリームに適用されるという具合になります

- `videoBitrates`パラメータが指定されていない場合、ビデオ関連のパラメータは無視されます

- `audioBitrates`パラメータが指定されていない場合、オーディオ関連のパラメータは無視されます


------

## 関連リンク

- [Transcode a Stream](userguide_transcode.html)

