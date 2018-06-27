---
title: イベントの概要
keyword: events
sidebar: api_sidebar
permalink: eventsoverview.html
folder: api
toc: true
---

EMSイベント通知システムを活用してEMSととてもパワフルなインタラクションができます。またサーバーの使用状況の把握と監視を簡単に行うことができます。ログをポーリングしたりパースができますし、EMSからのHTTPベースの通知をサブスクライブすることもできます。RESTfulモニタリングや統計情報収集が行えます。

イベント通知システムをつかって**カスタムストリーム処理**を作成することも可能です。たとえば新規インバウンドストリームにたいしてHLS/HDS/MSS/DASHを自動生成したい場合、“new inbound stream”イベントに呼応して`createHLSStream` / `createHDSStream` / `createMSSStream` / `createDASHStream`をコールするよう設定します。アウトバウンドストリームがロストした時に関連するインバウンドストリームを閉じたい場合、“outbound stream closed”イベントを受けたら`shutdownStream`をコールするよう設定します。

## イベント通知の設定

イベントは複数の宛て先（"sink"）に同時に送ることができます。sinkはファイルまたはネットワークの宛て先がとれます。複数のsinkが同時に有効化できますので、イベントをログにとりつつweb serviceも受け取るといったことができます。必要なイベントのみ発行するようsinkを設定することができます。イベントSinkは`config.lua`ファイルで設定されます

```
eventLogger=
{
    sinks=
    {
        type="sink1_type",
        -- property1 of sink1
        -- property2 of sink1
    },
    enabledEvents=
    {
        "inStreamCreated",
        "inStreamClosed",
    }
},
```



### Sinks

Sinkは"イベントの指定の宛て先"と定義され２つのタイプ: “ファイル” と"RPC”があります

Sinkではユーザーは *enabledEvents*アレイを定義できます。定義リストに記述されたイベントのみがsinkに送り込まれます。アレイが無い場合は全てのイベントがsinkに送られます。


### アプリケーション vs. サーバーイベント

config.luaファイルは次の２つのeventLoggerセクションがあります

1. Application-owned – application configurationセクションに記述されています。"application level"イベントを設定します。**この設定は編集していただいてよい**セクションです
2. Server-wide (またはデフォルト) – このセクションはアプリケーション外またはアプリケーションレベルが補足できないイベントの設定です。通常はサーバーの起動やシャットダウン、アプリケーションの読み込みなどのシステムイベント用の設定です



### イベントログの有効化

イベント通知はデフォルトではオフになっています。イベント通知システムを使用するには下記のようにEMS設定ファイルを編集する必要があります:

1.  eventLoggerセクションのコメント`--[[ ]]--`を取り除いてください
2.  ファイル名およびファイルフォーマットを選択してください
3.  使用する場合タイムスタンプを設定してください
4.  有効化するイベントを選択してください


## イベント Sinksタイプ

イベントsinkには**File Event Sink** と**Remote Procedure Calls Event Sink**２つの主要なタイプがあります。


### ファイル イベント Sink

ファイルsinkはイベントをファイルに書き込むもので"filename"パラメータで定義されます。システムロガーに似ています。ユーザーは書き出しフォーマットをJSON, XML, W3C, textなどから選択可能です。ファイルsinkはデフォルトで**off**となっており、`config.lua`内でsinkを記述してオンにすることができます

**Note:** EMSが起動する度にログ・ファイルは上書きされます

```
type="file",
filename="log.txt",
format="text",
customData="my custom data"
```

**ファイルsink設定:**

フォーマットは次のタイプのどれかを選択できます:

- “text” (プレーンテキスト) - テキストフォーマットは可読性の高い形でイベントファイルに書き込まれます

- “xml” - 各イベントファイルがXMLフォーマットで一行に書き込まれます

- “json” - 各イベントファイルがJSONフォーマットで一行に書き込まれます

- “w3c” - W3Cフォーマットファイルはスペースまたはタブ区切のコラムをもつ仕様に準拠しています。またコラム名を表記する(#)でコメントされたヘッダ行があります。


下記はファイルsinkの一般的な設定です:

```
eventLogger=
  {
      sinks=
      {
          {
              type="file",
              filename="../logs/events.txt",
              --format="text",
              --format="xml",
              --format="json",
              format="w3c",
              timestamp=true,
              appendTimestamp=true,
              appendInstance=true,
              fileChunkLength=43200, -- 12 hours (in seconds)
              fileChunkTime="18:00:00",
              enabledEvents=
              {
                  "inStreamCreated",
                  "outStreamCreated",
                  "streamCreated",
                  -- 中略
              },
              {
                  -- 中略

              },
          },
      },
  },
```

**Note:** config.luaでデフォルトでは無効にされています



#### ファイルSinkストラクチャ

|       Key       |  Type   | 必須か | 説明                              |
| :-------------: | :-----: | :-------: | ---------------------------------------- |
|   customData    | オブジェクト  |    no     | このsinkが生成するすべてのイベントに追加されるカスタムデータ。上位レベルでのカスタムデータ定義より優先されます。複雑な構造にすることも可能です |
|      type       | 文字列        |    yes    | sinkタイプ, “file”.                |
|    filename     | 文字列        |    yes    | ファイルのbase name |
|     format      | 文字列        |    yes    | ファイルフォーマット設定 “text”, “xml”, “json”, “w3c”が指定可 |
|    timestamp    | ブーリアン    |    no     | ファイル名にタイムスタンプを付加します                   |
| appendTimestamp | ブーリアン    |    no     | タイムスタンプ追加オプション設定 **true**の場合、タイムスタンプ (YYYYMMDD_HHmmSS)が全生成ログファイル名に付加されます。falseの場合は4桁の連番が付加されます。デフォルトは**true**です |
| appendInstance  | ブーリアン    |    no     | ランダムな４桁のインスタンスIDがログファイル名に追加されます。デフォルトはfalseです |
| fileChunkLength | 数値          |    no     | 新規ファイルが作成されるまでの秒数 |
|  fileChunkTime  | 文字列        |    no     | ログファイルをチャンクする時刻設定 HH:MM:SS フォーマットです。 **Note:** `fileChunkLength`および `fileChunkTime`両方ある場合はファイルチャンキングは行われません |
|  enabledEvents  | オブジェクト  |    no     | イベントがログに記録されます。セットされていない場合すべてログ記録されます。ただしW3Cではnon-stream-evventは無視されます |


上記のようにファイル名設定にはさまざまなオプションがありますが、下記に例を示します。


```
filename = "/var/evostreamms/logs/streams"
appendTimestamp = true
appendInstance = true
```
の場合、ログファイル名は `/var/evostreamms/logs/streams_0237_20140311_183046.txt`になります。



### RPC (リモートプロシージャコール)イベント Sink

HTTPベースのイベント通知を受けるにはRPCタイプsinkの定義が必要です(デフォルト)。URLパラメータは各イベントでコールされる場所を定義します。URLは特定のweb serviceスクリプトや、イベント処理するサービスが動作するIPアドレス・ポートなどに設定できます。RPC sinkは次の３つのシリアライザタイプ（HTTP post内フォーマット）を選択できます: JSON, XML, XMLRPC

イベントの詳細情報がHTTP postでリモートホストに転送され、EMSはリモートホストからのresponseは無視します

**RPC sink 設定:**

```
type="RPC",
url="http://192.168.1.5:5555/something/service",
serializerType="JSON",
customData="my custom data"
```

`url`フィールドにはHTTP postイベント通知を受ける宛て先を指定します

`serializer`タイプは次の３つのフォーマットのどれか:

- **JSON**

  JSONシリアライザタイプはXMLと同じスキーマでJSONとしてフォーマットされます

  ```
  {"payload":{"creationTimestamp":1349335053486.4370,"name":"","queryTimestamp":1349335053487.4370,"type":"NR","uniqueId":1,"upTime":1.0000},"type":"streamCreated"}
  ```

- **XML**

  XMLシリアライザはXMLスキーマを使い、よりEMSイベント通知システムに特化しています

  ```
  <?xml version="1.0" ?>
  <MAP isArray="false" name="">
      <MAP isArray="false" name="payload">
          <DOUBLE name="creationTimestamp">1349335287346.813</DOUBLE>
          <STR name="name"></STR>
          <DOUBLE name="queryTimestamp">1349335287346.813</DOUBLE>
          <STR name="type">NR</STR>
          <UINT64 name="uniqueId">1</UINT64>
          <DOUBLE name="upTime">0.000</DOUBLE>
      </MAP>
  <STR name="type">streamCreated</STR>
  </MAP>
  ```

- **XMLRPC**

  以前からあるXML-RPCスキーマのXMLフォーマット

  ```
  <?xml version="1.0"?>
  <methodCall>
      <methodName>event.Log</methodName>
      <params>
          <param>
              <value>
                  <struct>
                      <member>
                          <name>payload</name>
                          <value>
                              <struct>
                              <member>
                                  <name>creationTimestamp</name>
                                  <value><double>0.000000</double></value>
                              </member>
                              <!-- contents removed for clarity -->
                              </struct>
                          </value>
                      </member>
                      <member>
                          <name>type</name>
                          <value><string>streamCreated</string></value>
                      </member>
                  </struct>
              </value>
          </param>
      </params>
  </methodCall>
  ```


ファイルおよびRPCイベントsinkにおいて`customData`パラメータはオプションで使え、追加的データ記述用です。イベントを生成するEMSインスタンスを同定したり、イベント処理に関係する特定のIDやKeyを返したりするために使うことができます。`customData`パラメータはシンプルな文字列または複雑なLUAオブジェクトもとれます。

`customData`パラメータがノードで指定されていない場合、親`eventLogger` `customData` ノードの値が使用されますが、それも指定がなければ値はV_NULLとなります。

------

## Notes

- イベントsinkは有効化しなければ動作しません
- イベントログは設定された`ファイル名`で保存されます
- リストにイベントを追加・削除ができます
- 選択したイベントのみログに表示されます

------

## 関連リンク

- [List of Events](eventslist.html)

  ​