---
title: getStreamsCount
keywords: api
sidebar: api_sidebar
permalink: getStreamsCount.html
folder: api
toc: false
---



**アクティブ**なストリーム数を返します



## API パラメータ

パラメータはありません





## API Call テンプレート

```
getStreamsCount
```



### JSONのSuccess Response

```
{
"data":{
  "streamCount":1
  },
  "description":"Active streams count",
  "status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースするデータ
  - ​	streamCount – アクティブなストリーム数
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## 関連リンク

- [getStreamInfo](getStreamInfo.html)

