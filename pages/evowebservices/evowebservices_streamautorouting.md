---
title: Stream AutoRouting
keywords: webservices
sidebar: evowebservices_sidebar
permalink: evowebservices_streamautorouting.html
folder: evowebservices
toc: false
---


自動的にRTMP経由で他のEMSにストリームフォーワードしてくれるweb serviceです。新規ストリームがEMSに入ってくると、`pullStream`を送るか、またはEMSホストにストリームをプッシュしてくれます。このweb serviceはAPIコマンドを自動的に他のEMSに向けて送りストリームフォーワードします。

AutoRouting web serviceは、config.iniファイルで2つの設定値をとります。

1. **token** トークンが定義されており、空でない場合、AutoRouting web serviceはlocalStreamNameに"トークン"が含まれるストリームのみ転送します。

2. **destination_uri** ストリームを転送したいコンピュータのアドレス

   ```
       "StreamAutoRouter": {
           "plugin_switch": "enabled",
           "parameters": {
               "token": "stream",
               "destination_uri": "192.168.2.3"
           }
       },
   ```

上記の例では、“**stream**”がlocalstreamnameに含まれるストリームのみが、宛て先URIであるipアドレス*192.168.2.3*宛てに転送されます。

宛て先のサーバー上で`listStreams`コマンドで状況確認できます。

