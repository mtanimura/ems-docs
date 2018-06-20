---
title: getLicenseId
keywords: api
sidebar: api_sidebar
permalink: getLicenseId.html
folder: api
toc: false
---

使用中のライセンスのLicense IDを返します



## API パラメータ

パラメータはありません



## API Call テンプレート

```
getLicenseId
```



### JSONのSuccess Response

```
{
"data":{
"licenseId":"544247f0f6cca957"
},
"description":"getLicenseId",
"status":"SUCCESS"
}
```



#### JSON Response

JSON responseは以下を含みます:

- data – パースするデータ
  - licenseId - ライセンスID
- description– コマンドのパース・実行結果
- status – コマンドがパースされ正常実行された場合は**SUCCESS** そうでなければ**FAIL**

