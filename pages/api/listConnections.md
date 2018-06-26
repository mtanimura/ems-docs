---
title: listConnections
keywords: api
sidebar: api_sidebar
permalink: listConnections.html
folder: api
toc: false
---


すべてのアクティブなストリームに関係する接続についての情報を返します。EMS運用に使用される接続は含まれません(telnet、ライセンスマネージャ、インターフェース等)



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------------------: | :-----: | :-----------: | :---------------: | ---------------------------------------- |
| excludeNonNetworkProtocols | ブーリアン |     false     |      *null*       | 接続ID。通常は`listStreamsIds`の返り値 |



## API Call テンプレート

```
listConnections
```



### サンプル API Call

```
listConnections excludeNonNetworkProtocols=0
```



### JSONのSuccess Response

```
{
"data":[
    {
    "carrier":{
    "farIP":"54.239.131.147",
    "farPort":1935,
    "id":86,
    "nearIP":"192.168.2.107",
    "nearPort":45399,
    "rx":743036,
    "tx":3621,
    "type":"IOHT_TCP_CARRIER"
    },
    "pullSettings":{},
    "stack":[
        {
        "applicationId":0,
        "creationTimestamp":1448259304659.3040,
        "id":97,
        "isEnqueueForDelete":false,
        "queryTimestamp":1448259308424.6599,
        "type":"TCP"
        },
    …
    "txInvokes":5,
    "type":"OR"
    ]
    }
],
"description":"Available connections",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - carrier - 接続に関する詳細情報
    - farIp - far側のIPアドレス
    - farPort - far側の使用ポート
    - Id - サービスID
    - nearIp - ローカルコンピューターで使用されるIPアドレス
    - nearPort - ローカルコンピューターで使用されるポート
    - rx – この接続で受信したバイト総数
    - tx – この接続で転送されたバイト総数
    - type – 接続タイプ(TCP, UDP)
  - pullSettings/pushSettings/hlsSettings/hdsSettings/mssSettings/dashSettings/recordSettings – この接続の確立に使用されたストリームコマンドパラメータのコピー
    - 他のフィールドはそれぞれのストリームタイプにより異なります (`pushStream`, `pullStream`, `createHLSStream`, `createHDSStream`, `createMSSStream`, `createDASHStream`, `record` commandsを参照してください)
  - stack - 接続を使用している内部リソースに関する情報
    - applicationId - 接続を使用している内部アプリケーションID
    - creationTimeStamp - アプリケーションが接続の使用を開始した時間(UNIX秒)
    - Id - スタック関係のユニークID
    - isEnqueForDelete - 削除に使用する内部フラグ
    - queryTimeStamp - データがクエリーされた時間(UNIX秒)
    - rxInvokes – Number of received RTMP function invokes
    - streams – Details about the streams that are using the connection (see fields in`listStreams`)
    - txInvokes – Number of sent RTMP function invokes
    - type - アプリケーションの接続の使用についての記述子
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [getConnectionInfo](getConnectionInfo.html)
- [getConnectionsCount](getConnectionsCount.html)
- [getConnectionsCountLimit](getConnectionsCountLimit.html)

