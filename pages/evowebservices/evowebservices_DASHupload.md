---
title: Amazon S3 DASHアップロード
keywords: webservices
sidebar: evowebservices_sidebar
permalink: evowebservices_DASHupload.html
folder: evowebservices
toc: false
---


Amazon S3 ストレージインスタンスに自動的にDASHストリームをアップロードするweb serviceです。

EMSがディスクにDASH manifestチャンクを書き込むと、このweb serviceは自動的にAmazon S3インスタンスにそれらのチャンクをアップロードします。

Amazon S3アクセスおよび秘密鍵をconfig.iniに設定する必要があります。


1. **aws_access_key**. amazon aws s3 アクセスキー

2. **aws_secret_key**. amazon aws s3 秘密鍵

3. **default_bucket**. ファイルがアップロードされるamazon aws s3のbucket


   ```
       "AmazonDASHUpload": {
           "plugin_switch": "enabled",
           "parameters": {
               "aws_access_key": "1234567890",
               "aws_secret_key": "ABCDEFGHIJ1234567890",
               "default_bucket": "DASH_files",
           }
       },

   ```

上記の設定例では、生成されたすべてのDASHファイルは自動的にAmazon S3 の*DASH_files* bucketにアップロードされます。

**Note:** サービスが非稼働中に生成されたファイルはアップロードされません