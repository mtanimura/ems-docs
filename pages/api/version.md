---
title: version
keywords: api
sidebar: api_sidebar
permalink: version.html
folder: api
toc: false
---

フレームワークおよびアプリケーションのバージョンを返します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
version
```



### JSONのSuccess Response

```
{
"data":{
    "banner":"EvoStream Media Server (www.evostream.com) version 1.7.0 build 4242 with hash: 86bdcde75942b25390a15a6b1de521e913182bcf - PacMan|m| - (built for Ubuntu-14.04-x86_64 on 2015-11-18T10:54:56.000)",
    "branchName":"",
    "buildDate":"2015-11-18T10:54:56.000",
    "buildNumber":"4242",
    "codeName":"PacMan|m|",
    "hash":"86bdcde75942b25390a15a6b1de521e913182bcf",
    "releaseNumber":"1.7.0"
},
"description":"version",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースすべきデータ
  - banner – EMSバナー
  - branchName – パッケージのブランチ名
  - buildDate – リリースパッケージのビルド日付
  - buildNumber – リリースパッケージのビルド番号
  - codeName – リリースされたEMSバージョンのコード名
  - hash – リリースパッケージのハッシュ
  - releaseNumber – リリースパッケージのバージョン
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

