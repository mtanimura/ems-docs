---
title: removeConfig
keywords: api
sidebar: api_sidebar
permalink: removeConfig.html
folder: api
toc: false
---

ストリームを停止し、関連する設定エントリを削除します。このコマンドは`shutdownStream permanently=1`を行うのと同じです。



## API パラメータ




| パラメータ名  |  タイプ | 必須かどうか | デフォルト値 | 説明 |
| :---------------: | :-----: | :-------: | :-----------: | ---------------------------------------- |
|        id         | 整数値 |   true    |    *null*     | 削除される設定のconfigid。configidは`listConfig`で得ることができます インバウンドストリームを削除すると、関連するアウトバウンドストリームもすべて削除されます |
|     groupName     | 文字列  |   false   |    *null*     | 削除されるグループ名 (HLSやHDS、外部プロセスの場合にのみ適用) *idパラメータが指定されていない場合のみ必須* |
| removeHlsHdsFiles | ブーリアン |   false   |   0 *false*   | **true**でかつストリームがHLS または HDSの場合、関連するフォルダが削除されます |



## API Call テンプレート

```
removeConfig id=<configId>
```

または

```
removeConfig groupName=<groupName>
```



### サンプル API Call

```
removeConfig id=555
```



### JSONのSuccess Response

```
{
"data":{
    *..remove details for clarity*
    },
    "description":"Configuration terminated",
    "status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - configId – pullPushConfig.xmlエントリ用のid
  - 他フィールドはストリームタイプに依存
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

------

## Notes

- listConfigコマンドで表示されるconfig IDは、listStreamsコマンドで表示されるstream IDとは異なります。`removeConfig`コマンドはconfig IDを使います(stream IDではなく)




## 関連リンク

- [listConfig](listConfig.html)
- [getConfigInfo](getConfigInfo.html)