---
title: listTimers
keywords: api
sidebar: api_sidebar
permalink: listTimers.html
folder: api
toc: false
---

アクティブなタイマーをリストします



## API パラメータ

パラメータはありません



## API Call テンプレート

```
listTimers
```



### JSONのSuccess Response

```
{
  "data":[
    {
      "timerId":8,
      "triggerCount":141,
      "value":10
    }
  ],
  "description":"List of armed timers",
  "status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースするデータ
  - timerId – 追加されるタイマーID
  - triggerCount – タイマーがトリガーされた回数
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [setTimer](setTimer.html)
- [removeTimer](removeTimer.html)