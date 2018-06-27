---
title: enableService
keywords: api
sidebar: api_sidebar
permalink: enableService.html
folder: api
toc: false
---



serviceを有効化／無効化するコマンド



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :----------------: | :-----: | :-----------: | :---------------: | ---------------------------------------- |
|         id         | 整数値 |     true      |      *null*       | service id
|       enable       | ブーリアン |     true      |      *null*       | service有効化は**1** 無効化は **0**  |



## API Call テンプレート

```
enableService id=<serviceId> enable=<enableValue>
```



### サンプル API Call

```
enableService id=5 enable=0
```

idが5のサービスを**無効化します**

```
enableService id=5 enable=1
```

idが5のサービスを**有効化します**



### JSONのSuccess Response

```
{
          "data": {
                    "data": {
                              "acceptedConnectionsCount": 3,
                              "appId": 1,
                              "appName": "evostreamms",
                              "droppedConnectionsCount": 0,
                              "enabled": true,
                              "id": 5,
                              "ip": "0.0.0.0",
                              "port": 9556,
                              "protocol": "inboundRtmp,
                              "sslCert": "",
                              "sslKey": ""
                    },
                    "description": "Status changed",
                    "status": "SUCCESS"
          }
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - acceptedConnectionsCount – serviceを使用するアクティブ接続数
  - appId – serviceを使用するアプリケーションID
  - appName – serviceを使用するアプリケーション名
  - droppedConnectionsCount – ドロップした接続数
  - enabled - serviceが有効な場合は**true** そうでなければ**false**
  - id = serviceID
  - ip = serviceにバインドされたipアドレス
  - port – serviceにバインドされたポート
  - protocol – serviceにバインドされたプロトコル
  - sslCert – SSL証明書 (特定のプロトコルのみ)
  - sslKey – SSLキー(特定のプロトコルのみ)
  - useLengthPadding – Paddingが有効な場合**true** 、そうでない場合**false** (特定のプロトコルのみ)
  - waitForMetadata – メタデータが必要なら**true** 、そうでなければ **false** (特定のプロトコルのみ)
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [createService](createService.html)
- [listServices](listServices.html)
- [shutdownService](shutdownService.html)
- [acceptors](userguide_configlua.html#acceptors)