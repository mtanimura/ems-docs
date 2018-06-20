---
title: ERS API
keywords: html5
sidebar: html5players_sidebar
permalink: html5players_ersapi.html
folder: html5players
toc: true
---


ERS管理用APIをつかってトークンやroomの生成や削除ができます。APIはHTTP GETリクエスト経由で次のような書式でアクセスできます:

```
http(s)://<ERS IP>:<ERS adminPort>/?c=<commandName>&i=<Id>

```

**Where:**

| **フィールド**     | **内容**                          |
| ------------- | ---------------------------------------- |
| ERS IP        | ERSをホストするマシンのIPアドレス    |
| ERS adminPort | 管理APIがアクセスするポート番号 |
| commandName   | コマンド名               |
| Id            | トークンIDまたはroomID |

ERSとAPIを実行するマシンが同じ場合(デフォルト)、下記のような例になります:

```
http://127.0.0.1:3030/?c=addToken&i=thisIsASampleToken

```

上記のHTTP GETリクエストはさまざまなスクリプト言語から送ることができます

Javascriptをつかったサンプルの管理者インターフェースは以下のURLで参照できます:

```
http://127.0.0.1:3030/ersadmin.html
```



## APIリスト

### Version確認

ERSバージョンを返します.

| **フィールド**    | **値** |
| ------------ | --------- |
| コマンド名 | version   |
| パラメータID | (ignored) |

**APIコール**

```
http://127.0.0.1:3030/?c=version
```



### Tokenの追加

Adds a token that can be used later by a client trying to connect with EMS.

| **フィールド**    | **値**    |
| ------------ | ------------ |
| コマンド名 | addToken     |
| パラメータID | < token Id > |

**APIコール**

```
http://127.0.0.1:3030/?c=addToken&i=tokenId

```



### トークンの削除

トークンを削除します

| **フィールド**    | **値**    |
| ------------ | ------------ |
| コマンド名 | delToken     |
| パラメータID | < token Id > |

**APIコール**

```
http://127.0.0.1:3030/?c=delToken&i=tokenId

```



### Tokensのリスト表示

生成されたアクティブな全トークンを表示

| **フィールド**    | **値**  |
| ------------ | ---------- |
| コマンド名 | listTokens |
| パラメータID | (ignored)  |

**APIコール**

```
http://127.0.0.1:3030/?c=listTokens

```



### Roomの追加

ランタイムで許可されたroomをリストに追加します。またこのリストに無いroomの生成を妨げます。


| **フィールド**    | **値**   |
| ------------ | ----------- |
| コマンド名 | addRoom     |
| パラメータID | < room ID > |

**APIコール**

```
http://127.0.0.1:3030/?c=addRoom&i=roomId

```



### Roomの削除

Deletes a room added from the list.

| **フィールド**    | **値**   |
| ------------ | ----------- |
| コマンド名 | delRoom     |
| パラメータID | < room ID > |

**APIコール**

```
http://127.0.0.1:3030/?c=delRoom&i=roomId

```



### Roomsリスト表示

関連する情報およびステータスを含めすべてのroomをリスト表示


| **フィールド**    | **値** |
| ------------ | --------- |
| コマンド名 | listRooms |
| パラメータID | (ignored) |

**APIコール**

```
http://127.0.0.1:3030/?c=listRooms
```