---
title: Amazon S3 HLSアップロード
keywords: webservices
sidebar: evowebservices_sidebar
permalink: evowebservices_HLSupload.html
folder: evowebservices
toc: false
---


Amazon S3ストレージインスタンスにHLSストリームを自動的にアップロードしてくれるweb serviceです。

EMSがディスクにHLSチャンクを書き込むと、このweb serviceはAmazon S3インスタンスにファイルチャンクをアップロードします。

Amazon S3アクセスおよび秘密鍵をconfig.iniに設定する必要があります。


1. **aws_access_key**. amazon aws s3 アクセスキー

2. **aws_secret_key**. amazon aws s3 秘密鍵

3. **default_bucket**. ファイルがアップロードされるamazon aws s3のbucket

   ```
       "AmazonHLSUpload": {
           "plugin_switch": "enabled",
           "parameters": {
               "aws_access_key": "1234567890",
               "aws_secret_key": "ABCDEFGHIJ1234567890",
               "default_bucket": "HLS_files",
           }
       },

   ```

上記の設定例では、生成されたすべてのHLSファイルは自動的にAmazon S3 の*HLS_files* bucketにアップロードされます。

**Note:** サービスが非稼働中に生成されたファイルはアップロードされません
