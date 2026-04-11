---
url: https://engineering.dena.com/blog/2026/04/office-backup-line-dc-aggregation/
date: 2026-04-11
title: インターネット副回線のトラフィックをDCに集約してコスト削減した話
---

## 概要

DeNAの情報基盤部ネットワークグループが、オフィスの副回線を高額なダークファイバーからフレッツ光に変更し、NGN折り返し通信でデータセンターまでのトンネルを構築することでコスト削減を実現した事例。複数拠点の回線冗長化コストが月2〜3万円程度かかっていた課題に対し、安価なフレッツ光とNGN網内通信を組み合わせた低コスト・低遅延構成を実現した。初期はUbuntuサーバによるIPトンネル構成から始め、現在はJuniper SRXとVyOSを使った本運用体制に移行している。

## 主要ポイント

- 複数拠点の回線冗長化コストが月2〜3万円程度と高額で予算確保が困難だった
- ダークファイバーを廃止し、安価なフレッツ光を副回線として採用
- NGN網内での通信によりインターネットを経由せず低遅延を実現
- 初期構成はUbuntuサーバによるIPトンネルで検証
- 現構成はJuniper SRXとVyOSを使用した本運用体制
- ping_exporterをVyOS上で動作させPrometheusからメトリクスを取得する品質監視を実施
- VRF（Virtual Routing and Forwarding）の設定調整で疎通性を確保
- インフラコストの最適化とネットワーク冗長性の両立を達成

## キーワード

DeNA、フレッツ光、NGN、ダークファイバー、IPトンネル、Juniper SRX、VyOS、ping_exporter、Prometheus、VRF、SRE、インフラコスト削減
