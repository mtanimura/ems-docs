---
title: Stream Load Balancer
keywords: webservices
sidebar: evowebservices_sidebar
permalink: evowebservices_streamloadbalancer.html
folder: evowebservices
toc: true
---

Load Balancer web serviceを使うとEMSインスタンスグループが同じインバウンド(ソース)ストリームコレクションを維持します。

あるEMS上で新規ストリームが生成されると、Stream Load Balancer web serviceは他のすべてのEMSインスタンスにも同じストリームを取得するよう指示します。

Load Balancerが維持するEMSインスタンスのリストはconfig.iniファイルに定義されます。

1. **destination_ems_apiproxies** インバウンドストリームが複製されるipアドレスの配列。このパラメータについての詳細は、指定されたアドレス上のwebconfig.jsonに記述されています。

   ```
       "StreamLoadBalancer": {
           "plugin_switch": "enabled",
           "parameters": {
               "destination_ems_apiproxies": [
                   {
                       /* for Enabled API Proxy */
                       "enable" : true,
                       "authentication": "basic",
                       "pseudoDomain": "apiproxy",
                       "address": "192.168.2.3",
                       "ewsPort": 8888,
                       "userName": "username",
                       "password": "password"
                   },
                   {
                       /* for Disabled API Proxy */
                       "enable" : false,
                       "address": "192.168.2.4",
                   },
                   {
                       "enable" : true,
                       "authentication": "basic",
                       "pseudoDomain": "apiproxy",
                       "address": "192.168.2.6",
                       "ewsPort": 8888,
                       "userName": "username",
                       "password": "password"
                   }
               ]
           }
       },
   ```

   - **enable** - webconfig.jsonのapi proxy設定
   - **authentication** - 認証タイプ
   - **pseudoDomain** - apiproxy
   - **address** - ストリームが複製されるアドレス
   - **ewsPort** - そのアドレスのEWSポート
   - **userName** - api proxyが使用するそのアドレスのユーザ名
   - **password** - api proxyが使用するそのアドレスのパスワード

上記の設定例では、リストにある*(192.168.2.3, 192.168.2.4)* のサーバーipアドレスのサーバーすべてがホストEMSとして同じストリームをプルします。

これらのサーバー上で`listconfig` コマンドでストリーム条項を確認してください。すべてのストリームがプルされているはずです。


------

## Notes

- disabledおよびenabled設定を同時に使用することができます

- ユーザ名・パスワードが正しいことを確認してください

- 他の設定を追加する場合は、"}"の後の","を忘れないようにしてください。

- v2.0.0以下v2.0.0のAPI Proxyがdisableの場合に、v1.7.1のload balancerを使用することができます。


  ​



