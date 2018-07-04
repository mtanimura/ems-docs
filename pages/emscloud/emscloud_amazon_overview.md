---
title: Amazon Marketplace上でのEMS
keywords: amazon
sidebar: emscloud_sidebar
permalink: emscloud_amazon_overview.html
folder: emscloud
toc: false
---

Amazon EC2はコンピューティングリソースを仮想マシンとして仮想化するクラウドコンピューティングプラットフォームです。仮想マシンの設定はAmazon Machine Image(AMI)として登録されます。

EvoStreamは事前設定済みバージョンのEvoStream Media Serverを組み込んだAmazon Linux AMIを用意しており、Amazon Web Service (AWS) Management Consoleからすぐに使い始めることができます。このAMIを利用してEC2インスタンス用のEMSを起動でき、このインスタンスの実行時間および帯域消費に応じて課金されます。またこのインスタンスは視聴者により近い地域において起動することが可能ですので遅延を低減し、複数の拠点を利用することで冗長化がはかれます。

本文書はEvoStream Media ServerソフトウェアをAmazon Elastic Compute Cloud (Amazon EC2)上にインストールし設定する方法について記述しています。


## AWS Cloud上での低遅延ストリーミング

EvoStream Media Server (EMS)は高効率でスケーラブルなライブストリーミングメディアサーバーです。Amazon EC2インスタンス上でEMSを使用することで比類ない柔軟性・スケーラビリティが得られ、EMSやAmazonによるコスト低減や大規模同時ストリーミングが簡単に構築できることも大きなメリットです。低コストで構築にかかる時間も少なくて済みますので、ストリーミングプラットフォームの維持・拡大に寄与します。

EMSは以下の点で"**速さ**"を実現します

- CPUやメモリ使用における速さ：従来のJavaベースのソフトウェアにくらべ同一ハードウェア上で比較した場合４倍のストリーム数を扱えます。

- 運用までのスピード：HTTP経由でのEMSとJSONの統合。JavaScriptやPHP, Perl等利用可能で、EvoStreamはPHPのフリーサンプルを提供しており、一般的なインテグレーショントピックをカバーしています。

- ストリームの低遅延：RTSP, RTMP, MPEG-TS等でのサブセカンドでのエンドツーエンド配信

The Efficiency of the EMS is a critical cost-saving driver for platform operators. Doing more with fewer EC2 instances not only reduces instance up-time costs but it also reduces the amount of time and resources that are required to maintain such a platform. The EMS is 400% more efficient than conventional Java based solutions. This means that each EC2 instance running the EMS can handle the load of 4 conventional instances! The EMS can even be run on Micro instances. Use fewer instances, use smaller instances, save money, save time.

Integration with the EMS could not be simpler. The EMS provides a full Runtime API designed to be used with any server-side code. Send HTTP posts to the EMS to issue commands like pulling streams, pushing streams, generating security aliases, querying usage and much, much more. On the flip side, get automatically notified via HTTP and JSON when critical events happen: Stream is lost, new stream is present, DASH chunk completed and again, much, much more. These dual mechanism provide simple, flexible, and incredibly powerful ways to integrate using traditional RESTful server-side programming!

The low latency streaming of the EMS makes it ideal for many different types of devices and deployment models. EvoStream is often used by Action Sport camera and Wearables vendors for streaming live in Consumer, Prosumer and Enterprise applications. Whether the stream is being sent from a dirt-bike rider to a fan in the stands, or the EMS is enabling real-time-chat between a wearable operator and a back-end expert, low-latency is absolutely critical. The EMS is also deployed in many Security Camera NVR Systems providing real-time viewing of cameras across the internet (with NAT reach-back!).

The bottom line: Scale your business with EvoStream and the Amazon EC2 Marketplace while saving both time, resources AND money!



Read white paper [here](https://evostream.com/low-latency-streaming-on-aws-cloud/).

