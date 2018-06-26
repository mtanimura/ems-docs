---
title: addStorage
keywords: api
sidebar: api_sidebar
permalink: addStorage.html
folder: api
toc: false
---

新規ストレージを追加



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :-------------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|      mediaFolder      | 文字列  |   true    |    *null*     | メディアフォルダパス |
|      description      |  文字列  |   false   |    *null*     | ストレージの詳細情報 |
|   clientSideBuffer    | 整数値 |   false   |      15       | ファイルがストレージから再生されるさいクライエント側で保持すべきデータ量 |
|      enableStats      | ブーリアン |   false   |     false     | **true**の場合 メディアファイルが使用されると*.statsファイルが生成されます |
| externalSeekGenerator | ブーリアン |   false   |     false     | **true**の場合 *.seek と *.meta ファイルが外部ツールにより生成されます |
|     keyframeSeek      | ブーリアン |   false   |     false     | **true**の場合 キーフレームseekポイントを持つseek/metaファイルが生成されます |
|  maxPlaylistFileSize  | 整数値 |   false   |     4096      | プレイリストの最大サイズ |
|      metaFolder       | 文字列  |   false   |    *null*     | seek/metaファイルを保持するフォルダパス。指定がなければseek/metaファイルはメディアフォルダ内に生成されます
|         name          | 文字列  |   false   |    *null*     | ストレージ名 |
|    seekGranularity    | 整数値 |   false   |     1000      | シークファイルの粒度設定(ミリ秒) |



## API Call テンプレート

```
addStorage mediaFolder=<filePath/mediaFolderName> description=<storageDescription> name=<storageName>
```



### サンプル API Call

```
addStorage mediaFolder=C:/EvoStream/testMediaFolder description=testStorage name=anotherMediaFolder
```



### JSONのSuccess Response

```
{
"data":{
    "clientSideBuffer":15,
    "description":"TestStorage",
    "enableStats":true,
    "externalSeekGenerator":true,
    "keyframeSeek":true,
    "maxPlaylistFileSize":4096,
    "mediaFolder":"C:\\EvoStream\\testMediaFolder\\",
    "metaFolder":"C:\\EvoStream\\testMediaFolder\\",
    "name":"anotherMediaFolder",
    "seek Granularity":300000
},
"description":"Storage created",
"status":"SUCCESS"
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - clientSideBuffer – ファイルがストレージから再生されるさいクライエント側で保持すべきデータ量
  - description – ストレージの詳細情報
  - enableStats – **true**の場合 メディアファイルが使用されると*.statsファイルが生成されます
  - externalSeekGenerator – **true**の場合 *.seek と *.meta ファイルが外部ツールにより生成されます
  - keyframeSeek – **true**の場合 キーフレームseekポイントを持つseek/metaファイルが生成されます
  - maxPlaylistFileSize - プレイリストの最大サイズ
  - mediaFolder – メディアフォルダパス
  - metaFolder – seek/metaファイルを保持するフォルダパス、無ければthe seek/metaファイルはメディアフォルダ内に生成されます
  - name – ストレージ名
  - seekGranularity – シークファイルの粒度設定


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- 追加されたストレージはconfig.luaのメディアストレージには追加されません


------

## 関連リンク

- [mediaStorage](userguide_confuglua.html#mediastorage)
- [listStorage](listStorage.html)
- [removeStorage](removeStorage.html)

