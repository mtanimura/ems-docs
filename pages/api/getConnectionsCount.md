---
title: getConnectionsCount
keywords: api
sidebar: api_sidebar
permalink: getConnectionsCount.html
folder: api
toc: false
---

アクティブな接続数を返します。EMSオペレーションのための接続(telnet、ライセンスマネージャ、インターフェース等) やストリームによって開かれた接続(RTSP-UDP-RTP ports)も含まれます




## API パラメータ

パラメータはありません



## API Call テンプレート

```
getConnectionsCount
```



### JSONのSuccess Response

```
{
"data":{
    "count":3
},
"description":"Active connections count",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - count – アクティブな接続数
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [setConnectionsCountLimit](setConnectionsCountLimit.html)
- [getConnectionsCountLimit](getConnectionsCountLimit.html)