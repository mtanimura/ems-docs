---
title: getBandwidth
keywords: api
sidebar: api_sidebar
permalink: getBandwidth.html
folder: api
toc: false
---


現在の帯域設定値および制限値を返します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
getBandwidth
```



### JSONのSuccess Response

```
{
"data":{
    "current":{
    "in":111880.0459,
    "out":147.8026
	},
    "max":{
    "in":0.0000,
    "out":0.0000
    }
},
"description":"Bandwidth in B\/s",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - current – 現状の帯域
    - in – インバウンド帯域
    - out – アウトバウンド帯域
  - max – 最大帯域
    - in – インバウンドの制限値
    - out - アウトバウンドの制限値
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [setBandwidthLimit](setBandwidthLimit.html)