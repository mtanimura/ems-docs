---
title: help
keywords: api
sidebar: api_sidebar
permalink: help.html
folder: api
toc: false
---


API情報をJSONフォーマットでプリントします



## API パラメータ

パラメータはありません



## API Call テンプレート

```
help
```



### JSONのSuccess Response

```
{
“data":[
    {
    "command":"help",
    "deprecated":false,
    "description":"prints this help",
    "parameters":[]
    },
    {
    "command":"API",
    "deprecated":isdeprecated,
    "description":"API description",
    "parameters":[list of API parameters]
        {
        "defaultValue":parameter default value,
        "description":"parameter description”,
        "mandatory":ismandatoryparameter,
        "name":"parameter name"
        },
    },
    ],
"description":"Available commands",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - command – 有効なコマンド名
  - deprecated – **true**の場合コマンドは廃止予定です。**false** の場合そうではありません
  - description – コマンドの使用に関する情報
  - parameters – コマンドのパラメータ設定
    - defaultValue – パラメータが省略された場合のデフォルト値
    - description – パラメータの詳細
    - mandatory – **true**の場合パラメータは必須**false**はそうではない
    - name – コマンドパラメータ名
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

