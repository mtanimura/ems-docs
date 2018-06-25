---
title: Node.jsを利用したインストール
keywords: webservices
sidebar: evowebservices_sidebar
permalink: evowebservices_nodeinstall.html
folder: evowebservices
toc: false
---

## 事前に準備するもの

- Node.js
- npm
- EMS v2.0

## EvoWebservicesの取得

EvoWebservicesはEMSパッケージ2.0の中に含まれていますが、サービスのみ別途インストールすることもできます。

### Windowsでのインストール

1.evowebservices Windowsバッチファイルインストーラを [Github](https://github.com/EvoStream/evowebservices-archives/tree/master/installers)から **ダウンロード** してください。

2. .batファイルをダブルクリックしevowebservices **インストール** してください

   ```
   evowebservices-0.0.1-win-x64.bat
   ```

3. インストールがうまくいくと、下記のようにevowebservicesは自動的に起動されます

   ```
   starting evowebservices using npm....

   > evowebservices@0.0.0 start C:\node_evowebservices\node_modules\evowebservices
   > node ./bin/www

   STARTED: evowebservices:server Listening on port 4000
   info: STARTED: evowebservices:server Listening on port 4000
   info: Get enabled Plugins
   ```

   ​

### Linuxでのインストール

1.  [Github](https://github.com/EvoStream/evowebservices-archives/tree/master/installers)からevowebservices Bashスクリプトインストーラーを **ダウンロード** してください。

2.  インストーラーファイルを確認し、ターミナルで下記のようにスクリプトを実行し **インストール** してください:

   ```
   ./evowebservices-0.0.1-linux-x64.sh
   ```

3.  インストールがうまくいくと、下記のようにevowebservicesは自動的に起動されます

   ```
   Starting EVOWEBSERVICES...

   > evowebservices@0.0.0 start /home/user/Desktop/node_modules/evowebservices
   > node ./bin/www

   STARTED: evowebservices:server Listening on port 4000
   info: STARTED: evowebservices:server Listening on port 4000
   info: Get enabled Plugins
   ```

   ​
## EvoWebservicesの起動

EMS V2.0を起動すると、EvoWebserviceノードも自動的に起動されます。別途コンソール上でEvoWebserviceを起動したい場合は下記のようにしてください:


1. evowebserviceをEMSを起動させる前に実行してください。事前にconfig.luaでイベント通知システムやevowebservices用のプラグインの設定が完了していることを確認してください

2. ノードのコマンドプロンプトを開き、evowebserviceディレクトリに移動してください。下記のコマンドでevowebservicesを起動してください:

   ```
   npm start
   ```

**Note:** 
ノードのコンソールでevowebserviceのログをみてエラーが無いか確認できます。evowebservicesのログはevowebservices/logsディレクトリ以下にあります。




