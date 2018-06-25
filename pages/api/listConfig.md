---
title: listConfig
keywords: api
sidebar: api_sidebar
permalink: listConfig.html
folder: api
toc: false
---



全てのプッシュ／プル設定のリストを返します

`pullStream`または`pushStream`インターフェースがコールされた際にpullpushconfig.xmlファイルに詳細情報が記録されます。次回EMSが起動された際にpullpushconfig.xmlファイルが読み込まれ、すべてのプル／プッシュストリームの再接続が試行されます。



## API パラメータ

パラメータはありません



## API Call テンプレート

```
listConfig
```



### JSONのSuccess Response

```
{
"data":{
    "dash":[details of dash streams],
    "hds":[details of hds streams],
    "hls":[details of hls streams],
    "metalistener":[details of metalistener added],
    "mss":[details of mss streams],
    "process":[details of on process commands sent],
    "pull":[details of pulled streams],
    "push":[details of pushed streams],
    "record":[details of recorded streams],
    "webrtc":[details of started webRTC channels]
    },
"description":"Run-time configuration",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - dash -  [`createDASHStream`](createDASHStream.html)の詳細情報
  - hds -  [`createHDSStream`](createHDSStream.html)の詳細情報
  - hls -  [`createHLSStream`](createHLSStream.html)の詳細情報
  - metalistener -  [addMetadataListener](addMetadataListener.html)の詳細情報
  - mss -  [`createMSSStream`](createMSSStream.html)の詳細情報
  - process -  process commandsの詳細情報
  - pull -   [`pullStream`](pullStream.html)の詳細情報
  - push -  [`pushStream`](pushStream.html)の詳細情報
  - record -  [`record`](record.html)の詳細情報
  - webrtc -  [`startWebrtc`](startWebRTC.html)

- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- `keepAlive`が**true**の設定のみリストされます
- アクティブな設定のみリストされます

------

## 関連リンク

- [removeConfig](removeConfig.html)
- [getConfigInfo](getConfigInfo.html)