---
title: Virtual Machineの作成
keywords: azure
sidebar: emscloud_sidebar
permalink: emscloud_azure_createVM.html
simple_map: false
map_name: usermap
box_number: 1
folder: emscloud
---

## はじめに

### 事前準備

- Microsoftアカウントが必要です

## 構築

Azure上でEvoStream Media Serverをはじめるには、まず仮想マシンのセットアップが必要となります。下記の**Quick Deploy**および **仮想マシンのセットアップ** を参照し仮想マシンを用意してください。


### A.	Quick Deploy

To lessen the time of configuring a virtual machine, clicking the links below will navigate you to the Custom Deployment Template.

- _Quick-Deploy: 下記の手順１および２は次のボタンのどちらかをクリックするだけでスキップすることができます:_
  - _Quick-Deploy EvoStream Media Server 1.7.1 for Windows Server 2012 R2_
    <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FEvoStream%2Fevostream_addons%2Fmaster%2Fazure_templates%2Fems171_windows2012%2Fazuredeploy.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/></a>
  - _Quick-Deploy EvoStream Media Server 1.7.1 for Ubuntu 14.04 64-bit_
    <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FEvoStream%2Fevostream_addons%2Fmaster%2Fazure_templates%2Fems171_ubuntu1404%2Fazuredeploy.json" target="_blank"><img src="http://azuredeploy.net/deploybutton.png"/></a>

**Note:** このセットアップで使用されるマシンサイズは A5 Standardです

​	![](images/emscloud/A5.jpg)

### B.	仮想マシン環境のセットアップ

1. Azure marketplaceでEvoStream Media Serverを検索するか、または[リンク](https://azure.microsoft.com/en-us/marketplace/partners/evostream-inc/evostream-media-server/)をクリックして先に進みます

   ![](images/emscloud/homepage.JPG)

2. 仮想マシンのOSを選択し、 **Create Virtual Machine** ボタンをクリックしてください

   ![](images/emscloud/OSselect.jpg)

   **利用可能なイメージ**

   - EvoStream Media Server for Windows - Windows Server 2012 R2
   - EvoStream Media Server for Ubuntu - Ubuntu 14.04 64-bit

3. Microsoft Azureアカウントに**サインイン**してください。EvoStream Media Serverページにリダイレクトされます。 **Create**ボタンをクリックしてください

   ![](images/emscloud/create_windows.JPG)

4. 用途に応じて仮想マシンの設定を行ってください:

   - 基本設定

   ![](images/emscloud/basics.jpg)


   - 仮想マシンサイズ選択

         **Note:** View allをクリックして利用可能なマシンサイズを表示させることができます

        ![](images/emscloud/size.jpg)


   - オプション機能の設定

  ![](images/emscloud/optional.jpg)


   - 設定項目の確認
  ![](images/emscloud/summary.jpg)


   - 購入
  ![](images/emscloud/buy.jpg)

5. **Settings**, **Offer Details**、 **Terms of Use** を確認し、 **Purchase** ボタンをクリックするとdeployが行われます。

6. イメージが作成されたか確認するには**Microsoft Azure Dashboard**で**Virtual machines**をクリックしてください。うまくいくと作成されたイメージが表示されます

**Note:** deployment後にマシンは起動されます


