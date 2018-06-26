---
title: setLogLevel
keywords: api
sidebar: api_sidebar
permalink: setLogLevel.html
folder: api
toc: false
---

全てのLog Appenderのログレベルを変更します。デフォルト値は通常6にセットされておりconfig.luaファイルに設定されています。



## API パラメータ

| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :------------: | :-----: | :-------: | :-----------: | -------------------------------- |
|     level      | 整数値 |   true    |    *null*     | **-1** から **6**までの整数値 |



## API Call テンプレート

```
setLogLevel level=1
```

This sets the log level to 1. It means it will only output the error logs.



### JSONのSuccess Response

```
{
"data":null,
"description":"Log level is set",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータはありません


- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- ログレベル:
  - 0 – Fatal
  - 1 – Error
  - 2 – Warning
  - 3 – Info
  - 4– Debug
  - 5 – Fine
  - 6 – Finest
  - -1 - Disabled




## 関連リンク

- [logAppenders](userguide_configlua.html#logappenders)