---
title: listInboundStreamNames
keywords: api
sidebar: api_sidebar
permalink: listInboundStreamNames.html
folder: api
toc: false
---

現在のインバウンド `localStreamNames`のリストを提供します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
listInboundStreamNames
```



### JSONのSuccess Response

```
{
"data":[
  {
  "name":"teststream1"
  },
  {
  "name":"teststream2"
  },
  {
  "name":"teststream3"
  }
],
"description":"Inbound local stream names",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - name - インバウンドストリームの`localStreamName`
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [listInboundStreams](listInboundStreams.html)