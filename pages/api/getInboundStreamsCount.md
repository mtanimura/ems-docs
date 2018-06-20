---
title: getInboundStreamsCount
keywords: api
sidebar: api_sidebar
permalink: getInboundStreamsCount.html
folder: api
toc: false
---

アクティブなインバウンドストリーム数を返します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
getInboundStreamsCount
```



### JSONのSuccess Response

```
{
"data":{
  "inboundStreamsCount":3
  },
  "description":"Active inbound streams",
  "status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースするデータ
  - inboundStreamsCount - アクティブなインバウンドストリーム数


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [listInboundStreams](listInboundStreams.html)
- [listInboundStreamNames](listInboundStreamNames.html)