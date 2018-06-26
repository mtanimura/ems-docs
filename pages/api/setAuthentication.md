---
title: setAuthentication
keywords: api
sidebar: api_sidebar
permalink: setAuthentication.html
folder: api
toc: false
---

RTMP認証の有効／無効設定



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|    enabled     | ブーリアン |   true    |    *null*     | **1** が認証有効、**0**が認証無効 |



## API Call テンプレート

```
setAuthentication enabled=1
```



### JSONのSuccess Response

```
{
"data":{
    "enabled":true
},
"description":"Authentication mode updated",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - enabled – **true**の場合認証は有効 **false** は無効


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [Adding Stream Authentication](userguide_addstreamauth.html)