---
title: removeTimer
keywords: api
sidebar: api_sidebar
permalink: removeTimer.html
folder: api
toc: false
---

設定中のタイマーを削除します



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :-----: | :-------: | :-----------: | --------------------------------- |
|       id       | 整数値 |   true    |     null      | 削除するタイマーID |



## API Call テンプレート

```
removeTimer id=<id>
```



### サンプル API Call

```
removeTimer id=8
```



### JSONのSuccess Response

```
{
  "data":{
    "timerId":8,
    "triggerCount":0,
    "value":10
  },
  "description":"Timer removed",
  "status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - Id – タイマーID
  - triggerCount – 追加されてからタイマーがトリガされた回数
  - value – タイマーの設定値

- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## 関連リンク

- [setTimer](setTimer.html)
- [listTimers](listTimers.html)