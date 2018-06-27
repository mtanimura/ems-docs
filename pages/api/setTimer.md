---
title: setTimer
keywords: api
sidebar: api_sidebar
permalink: setTimer.html
folder: api
toc: false
---

タイマーを追加します。トリガーされるとevent loggerにイベントが送られます



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :----: | :-------: | :-----------: | ---------------------------------------- |
|     value      | 文字列 |   true    |     null      | タイマーの設定値。タイマーがトリガされる絶対時間 **(YYYY-MM-DDTHH:MM:SS または HH:MM:SS)** で設定するかまたは、**1**秒から**86399**秒おきまで、期間(最長１日)で設定  |



## API Call テンプレート

```
setTimer value=<value>
```



### サンプル API Call

```
setTimer value=10
```

```
setTimer value=2016-10-21T07:30:00
```

```
setTimer value=07:30:00
```

### JSONのSuccess Response

```
{
  "data":{
    "timerId":8,
    "triggerCount":0,
    "value":10
  },
  "description":"Custom timer enqueued",
  "status":"SUCCESS"
}
```

```
{
  "data":{
    "timerId":9,
    "triggerCount":0,
    "value":2016-10-21T07:30:00.000
  },
  "description":"Custom timer enqueued",
  "status":"SUCCESS"
}
```

```
{
  "data":{
    "timerId":10,
    "triggerCount":0,
    "value":2016-10-13T07:30:00.000
  },
  "description":"Custom timer enqueued",
  "status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - Id – 追加されたタイマーID
  - triggerCount – 追加されてからタイマーがトリガされた回数
  - value – タイマーの設定値

- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**


------

## Notes

- **HH:MM:SS** を使用する場合トリガは**今日**の指定時間という意味です


------

## 関連リンク

- [listTimers](listTimers.html)
- [removeTimer](removeTimer.html)