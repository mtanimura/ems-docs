---
title: Deploying EMS Instance
keywords: amazon
sidebar: emscloud_sidebar
permalink: emscloud_amazon_deployinstance.html
folder: emscloud
toc: true
---




## 使い始める

### 事前準備

- Amazon Web Services のアカウント
- Amazon EC2 Console のアカウント

### フリー試用版

EMSは30日間のフリーの評価版を提供しています

![](images/emscloud/image12.png)

**Note:** EMSのフリー評価版はフリーですが、AWSインフラの利用は課金されます

## 構築

Amazon EC2上でEvoStream Media Server (EMS)の利用をするためにはまずAmazon Web Services[website](https://aws.amazon.com/marketplace)でEMSインスタンスを購入する必要があります。

1. AWS marketplaceでEvoStream Media Serverを検索するか、 [リンク](https://aws.amazon.com/marketplace/pp/B00VTR946Y)をクリックしてください

   ![](images/emscloud/image1.JPG)

2. **Continue**をクリックし、AWSアカウントに**Sign in**してください

   ![](images/emscloud/image2.png)

3. EMSインスタンスタイプを選択してください: *(1-Click Launch か Manual Launch)*

- ### 1-Click Launch

  ![](images/emscloud/image3.jpeg)

  Amazon 1-click Launchユーティリティによりインスタンスセットアップは簡単に行えます。EMSはデフォルト設定が適用された状態で構築されます

  A.EMSの **Version** を選択してください

  ![](images/emscloud/image4.JPG)

  B. *Region** および**EC2 Instance Type** (コンピュータサイズ)を選択してください

  ![](images/emscloud/region.jpg)

  ![](images/emscloud/image5.JPG)

  **Note:** EMSはMicro EC2インスタンスなど小規模コンピュータ上でも実行可能です。インスタンスのサイズはホスティングするトラフィック規模が直接影響されます。通常仮想マシンのCPUやメモリを使い切る前に帯域を使い切ってしまうケースがほとんどです。

  C. **VPC** および **Subnet** を選択・作成してください

  ![](images/emscloud/image6.JPG)

  **Note:** 詳しくは [VPC](http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Introduction.html)を参照してください

  D. **Security Group**を選択してください

  ![](images/emscloud/image7.JPG)

  デフォルトセキュリティグループはストリーミングに使用する全ポートへの外部アクセスを提供するようデザインされており、ポートは下記のように定義されています:

| **ポート** | **用途**                          |
| -------- | ----------------------------------- |
| 1112     | Telnet for API (JSON)               |
| 1113     | (Internal use only)                 |
| 1222     | Telnet for API (ASCII)              |
| 1935     | RTMP                                |
| 1936     | (内部使用)                 |
| 22       | SSH                                 |
| 3389     | RDP                                 |
| 4443     | RTMP                                |
| 5000     | (Reserved)                          |
| 5544     | RTSP                                |
| 5985     | (Reserved)                          |
| 6666     | Live FLV                            |
| 7777     | HTTP for API                        |
| 8080     | HTTP Requests                       |
| 8100     | JSON META                           |
| 8210     | WS JSON META                        |
| 8410     | WS FMP4                             |
| 8888     | HTTP for EWS (EvoStream Web Server) |
| 9999     | MPEG TS                             |

これらのセキュリティ設定は変更可能ですが、サーバーのストリームアクセシビリティに影響がおよびます。


**Note:** 詳しくはアマゾンの [Security Group](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#default-security-group)をご参照ください

E.	**Key Pair**の選択・作成

![](/images/emscloud/image8.JPG)

インスタンスへのアクセスに既存のkey pairを選択するかアカウント用に新規に作成してください。既存のペアを選択する場合.pemファイルをダウンロード済みであることを事前に確認してください。Amazonはkey pairの２回目のダウンロードを許可しません。

**Note:** くわしくはアマゾンの[Key Pairs](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html) をご参照ください



F.	作成した設定を再度確認し、**Launch with 1-Click**をクリックして起動してください

![](images/emscloud/image9.jpeg)

- ### Manual Launch

![](images/emscloud/image10.jpeg)

**Step 1: AMIの選択**

A.	利用する**EMS version**を選択してください

![](images/emscloud/image11.JPG)

B.	選択**Region**の**Launch with EC2 Console** をクリックしてください

![]../images/emscloud/region_man.JPG)

**Step 2: Instance Typeの選択**

**Launch Instance Wizard in Step 2**にリダイレクトされます。

C.	Select the **Instance Type**を選択してください。**Review and Launch**または**Next**をクリックし設定を継続してください

![](images/emscloud/instancetype.JPG)

**Step 3: インスタンスの詳細設定**

D.	必要に応じてインスタンスの設定をおこなってください。**Review and Launch**か**Next**をクリックし設定を続けてください

![](images/emscloud/instance.JPG)

**Step 4: ストレージの追加**

E.	**Add New Volume** をクリックするかAMIの**Review and Launch** または **Next** をクリックして設定を継続してください

![](images/emscloud/volume.JPG)

F.	インスタンスにタグを付加するかまたはAMIの**Review and Launch** または**Next**をクリックして設定を継続してください

![](images/emscloud/tag.JPG)

G.	使用する**security group**を**Create** または **select**し、**Review and Launch**をクリックしてください

![](images/emscloud/securitygroup.JPG)

**Step 7: Review and Launch**

H.	設定を再確認し、必要なら修正をおこない、その後 **Launch**してください

![](images/emscloud/review.JPG)

I.	keyのプロンプトウインドウが表示されます。既存のキーペアを選択または新規作成し、**Launch instances**をクリックしてください

![](images/emscloud/keypair.jpg)

**Note:** **Instances Menu**でインスタンスが作成されたことが確認できます



