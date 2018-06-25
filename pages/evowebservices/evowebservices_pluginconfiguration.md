---
title: EMS Web Serviceプラグインの設定
keywords: webservices
sidebar: evowebservices_sidebar
permalink: evowebservices_pluginconfiguration.html
folder: evowebservices
toc: false
---


EMS Web Serviceは“**plugin**”内に含まれています。各プラグインは各web serviceに合わせて有効化・無効化することができます。EMS Web Serviceシステムは多くのWeb Service Pluginを一度に動作させることができ、一連の機能を作成することができます。



## A. 設定ファイル (config.ini/plugins.json)

EMS Web Servicesではプラグイン用の主要な設定ファイルがあります

**場所:** evowebservices > config > plugins.json

**disabled**から**enabled**に変更することでプラグインを有効化します。デフォルトではすべてのプラグインはdisableになっています。

プラグインの設定:

```
"plugin_switch": "enabled",
```



## B. ログ (logging.json)

ノード上でのみ使用可能。evowebservicesログファイル・ログコンソール用の設定ファイルです。
 **evowebservices > config > logging.json** にあります。

ログの設定オプション:

```
{
  "options": {
    "level": "silly",
    "handleExceptions": true,
    "json": false,
    "maxsize": 5242880
  }

```

- level - ログレベル

  下記のように６種のデフォルトレベルがあります:

  ```
  level 0 = silly (lowest)
  level 1 = debug
  level 2 = verbose
  level 3 = info
  level 4 = warn
  level 5 = error (highest)

  ```

- handleExceptions - winstonでUncaught Exceptionsを処理

- json - ログ・ファイルはjsonフォーマットまたはstringフォーマットで記述されます

- maxsize - ログファイルの最大サイズ(KB)