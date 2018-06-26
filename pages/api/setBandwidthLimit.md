---
title: setBandwidthLimit
keywords: api
sidebar: api_sidebar
permalink: setBandwidthLimit.html
folder: api
toc: false
---


入出力帯域制限を設定します



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|       in       | 整数値 |   true    |    *null*     | 最大入力帯域。**0**は無効 CLI接続には影響はおよびません |
|      out       | 整数値 |   true    |    *null*     | 最大出力帯域。**0**は無効 CLI接続には影響はおよびません |





## API Call テンプレート

```
setBandwidthLimit in=<maximumInputValue> out=<maximumOutputValue>
```



### サンプル API Call

```
setBandwidthLimit in=400000 out=300000
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
    "in":400000.0000,
    "out":300000.0000
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
  - max – 最大帯域値
    - in – インバウンド制限値
    - out - アウトバウンド制限値
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [getBandwidth](getBandwidth.html)
- [Configuring Bandwidth Limits](userguide_bandwidthlimits.html)