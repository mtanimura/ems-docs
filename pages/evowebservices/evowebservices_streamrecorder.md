---
title: Stream Recorder
keywords: webservices
sidebar: evowebservices_sidebar
permalink: evowebservices_streamrecorder.html
folder: evowebservices
toc: false
---


Stream RecorderはEMSにストリームを録画するよう指示します。

新規ストリームが生成されると、Stream Recorder web serviceはAPIコマンドを発行し、ストリームをmp4フォーマットで録画保存します。秒単位でどれくらいの時間録画するかも設定可能です。

録画したファイルの保存先をconfig.iniファイルで設定する必要があります。

1. **file_location** 録画ファイルの保存先

   **Notes:**

   - 絶対パスを使用してください
   - Windows OSを使用する場合はフォルダ区切りにダブルスラッシュ(//)を使用してください

2. **period_time**  秒単位(1~86399)で録画時間を設定してください。最大値は86399(24時間)です。

   ```
       "StreamRecorder": {
           "plugin_switch": "enabled",
           "parameters": {
               "file_location": "C:\\EvoStream\\media",
               "period_time": 3600
           }
       },
   ```

上記の設定例では、EMSでプルしたすべてのストリームを自動的に指定のパスに各ファイル3600秒間(60分)録画します（プラグイン・ストリームが有効な場合に限り）
