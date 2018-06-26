---
title: listStorage
keywords: api
sidebar: api_sidebar
permalink: listStorage.html
folder: api
toc: false
---

書き込み可能なメディアストレージの場所をリスト表示



## API パラメータ

パラメータはありません



## API Call テンプレート

```
listStorage
```



### JSONのSuccess Response

```
{
"data":[
    {
    "clientSideBuffer":15,
    "description":"Default media storage",
    "enableStats":false,
    "externalSeekGenerator":false,
    "keyframeSeek":true,
    "maxPlaylistFileSize":4096,
    "mediaFolder":"\/home\/evo\/Desktop\/evostreamms-1.7.0.4242-x86_64-Ubuntu_14.04\/media\/",
    "metaFolder":"\/home\/evo\/Desktop\/evostreamms-1.7.0.4242-x86_64-Ubuntu_14.04\/media\/",
    "name":"0x00000001",
    "seekGranularity":1000
    }
    ],
"description":"Available storages",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - clientSideBuffer – ストレージからファイルが再生される際クライエント側で保持すべきデータ量
  - description – ストレージの詳細情報
  - enableStats – **true**の場合、メディアファイルが使用されると*.statsファイルが生成されます
  - externalSeekGenerator – **true**の場合、*.seek や *.metaファイルが外部ツールによって生成されます
  - keyframeSeek – **true**の場合、１キーフレームseekポイントを持つseek/metaファイルが生成されます
  - maxPlaylistFileSize - プレイリストの最大サイズ
  - mediaFolder – メディアフォルダのパス
  - metaFolder – seek/metaファイルを保持するフォルダパス。指定がなければseek/metaファイルはメディアフォルダ内に生成されます
  - name – ストレージ名
  - seekGranularity – シークファイルの粒度設定
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [addStorage](addStorage.html)
- [removeStorage](removeStorage.html)
- [mediaStorage](userguide_confuglua.html#mediastorage)