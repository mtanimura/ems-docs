---
title: getExtendedConnectionCounters
keywords: api
sidebar: api_sidebar
permalink: getExtendedConnectionCounters.html
folder: api
toc: false
---


ネットワーク記述子カウンターに関する詳細情報を返します。異なる接続タイプでの最大値履歴や累積値などが含まれます。





## API パラメータ

パラメータはありません



## API Call テンプレート

```
getExtendedConnectionCounters
```



### JSONのSuccess Response

```
{
"data":{
    "origin":{
    "grandTotal":{
        "current":22,
        "inBytes":258381745,
        "inSpeed":0.0000,
        "max":24,
        "outBytes":350990,
        "outSpeed":0.0000,
        "total":304
        },
    "managedNonTcpUdp":{
        --removed content for clarity
        },
    "managedTcp":{
        --removed content for clarity
        },
    "managedTcpAcceptors":{
        --removed content for clarity
        },
    "managedTcpConnectors":{
        --removed content for clarity
        },
    "managedUdp":{
        --removed content for clarity
        },
    "rawUdp":{
    "current":0,
    "inBytes":0,
    "max":0,
    "outBytes":0,
    "total":0
    }
    },
    "total":22
},
"description":"Connection counters",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - origin
    - grandTotal – 全接続の統計情報
    - managedNonTcpUdp – non-TCP/UDP接続の統計情報
    - managedTcp – TCP接続の統計情報
    - managedTcpAcceptors – TCP acceptorsの統計情報
    - managedTcpConnectors – TCP connectorsの統計情報
    - managedUdp – UDP connectionsの統計情報
    - rawUdp – raw UDPの統計情報
  - Total – 総接続数

- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

