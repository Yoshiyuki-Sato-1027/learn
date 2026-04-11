---
url: https://dev.classmethod.jp/articles/amazon-s3-files-pricing-visual-guide/
date: 2026-04-11
title: Amazon S3 Files の料金体系を図解で整理してみた
---

## 概要

Amazon S3 FilesとEFSの料金体系を図解を使ってわかりやすく解説するクラスメソッドの技術記事。S3 FilesはEFSをベースにしながらS3バケットとNFSクライアント間にキャッシュ層（高性能ストレージ）を置く構成で、メタデータとアクティブデータのみを保持しS3と定期同期する仕組みを持つ。sizeLessThanの閾値（デフォルト128KB）によってファイルの扱いが変わり、大規模データでアクティブ比率が低いワークロードではEFSと比較してコストを大幅に下げられる可能性がある。

## 主要ポイント

- S3 FilesはEFSをベースとしたキャッシュ層（高性能ストレージ）で、S3バケットとNFSクライアント間に位置する
- メタデータとアクティブデータのみをキャッシュ層に保持し、S3と定期的に同期する構成
- 高性能ストレージの料金は$0.36/GB/月（東京リージョン）
- データ読み取り：$0.04/GB（閾値未満ファイル）、データ書き込み：$0.07/GB
- `sizeLessThan`設定（デフォルト128KB）により、閾値未満のファイルはストレージに保存され、以上のファイルはS3から直接ストリーミングされる
- S3 Files + Intelligent-TieringとEFS Elastic Throughputを比較すると、大規模データでアクティブ比率が低いワークロードではS3 Filesのコストが大幅に低くなる
- NFS互換のインターフェースでS3への低レイテンシアクセスを実現

## キーワード

Amazon S3 Files、EFS、高性能ストレージ、NFS、Intelligent-Tiering、sizeLessThan、キャッシュ層、料金比較、クラスメソッド
