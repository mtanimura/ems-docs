---
title: EMSインスタンスの停止／終了
keywords: amazon
sidebar: emscloud_sidebar
permalink: emscloud_amazon_stopEMS.html
folder: emscloud
toc: false
---


Amazonによると, *"インスタンスがAmazon EBSボリュームをルートデバイスとして持つ場合にインスタンスの停止やリスタートを行うことができます"*

EMSを使用しなくなったら、不要な課金を防ぐためインスタンスを停止または削除することを推奨します。インスタンスを削除するとそのサーバー上に保存したファイル等もすべて削除されます。こうしたファイルを保存しておきたい場合はインスタンスを削除する前にAmazon Simple Storage Service (Amazon S3)に保存しておいてください。

データを保存したら、次の手順でインスタンスの停止・削除を行えます:

1. AWSアカウントに**Log in**してください
2. NavigationペインのInstancesで**Instances**をクリックしてください
3. 削除したい実行中のインスタンスを選択してください
4. Click the **Actions**ボタンをクリックし、**Stop**または**Terminate**ボタンをクリックしてください。Instance State欄にインスタンスがシャットダウンまたは削除されたことが表示されます
   ![](images/emscloud/stopter.jpg)

- **EMS Stopped Instance**
  ![](images/emscloud/stop.jpg)

- **EMS Terminated Instance**
  ![](images/emscloud/terminate.jpg)

**Note:** Amazonはサインアウト前にマシンが削除ステータスになったことを確認するよう推奨しています。インスタンスシャットダウンに失敗していると課金は続いてしまいます。詳しくは[ここ](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Stop_Start.html)のAmazonのドキュメントを参照してください