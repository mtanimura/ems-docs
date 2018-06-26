---
title: removeStorage
keywords: api
sidebar: api_sidebar
permalink: removeStorage.html
folder: api
toc: false
---

ストレージの場所を削除します



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :----: | :-------: | :-----------: | ---------------------------- |
|  mediaFolder   | 文字列 |   true    |    *null*     | メディアフォルダパス |



## API Call テンプレート

```
removeStorage mediaFolder=<targetFolderPath>
```



### サンプル API Call

```
removeStorage mediaFolder=C:\EvoStream\testMediaFolder
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
"description":"Storage removed",
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

- ストレージを削除してもconfig.luaファイルのストレージ設定は削除されません


------

## 関連リンク

- [listStorage](listStorage.html_)
- [addStorage](addStorage.html)
- [mediaStorage](userguide_confuglua.html#mediastorage)