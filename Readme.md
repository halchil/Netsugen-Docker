# はじめに
6/21 Netsugen Dockerセミナーにご参加いただきありがとうございます。

# ワークショップの目的
本ワークショップの目的は、Dockerを活用して理想的なシステムを自ら構築する力を身につけること。

そのために、dockerコマンドの使い方や、マニフェストファイル（Dockerfileやdocker-compose.yml）の記述方法を操作を通じて学習する。

参加者は、基礎的なコンテナ操作から始め、最終的には自身のシステム構成を設計・実装することを目指す。

# 本リポジトリを有効活用するための前提条件

このリポジトリでは、Dockerfileや各種コマンドの記述方法・使用方法について具体的に解説していますが、それらを実際に動かして学ぶには、動作環境となるサーバやDockerの実行環境が不可欠となる。

実際に手を動かしてDockerによるシステム構築を体験することで、応用力を高めることができる。

そのため、リポジトリを最大限に活用するために、あらかじめ前提となる環境を整えておくことが重要となる。

以下に、最低限必要となる前提条件をまとめている。


## サーバ環境

・グローバルまたはプライベートネットワーク内でアクセス可能なIPアドレス (またはDNS名)が付与されていること

・Linux系OS(Ubuntu・CentOSなど)での利用を想定
（Windows/Mac は WSL または仮想環境でも可）

## ソフトウェア環境
・Dockerがインストール済みであること(`docker --version`コマンドで確認)

・ファイアウォールは無効化されていること(またはすべてのポートが開放されていること)

※ワークショップ中は複数のポートを使用する可能性があるため、アクセス制限がないことが望ましい


# トレーニングの概要

## Work1 Nginx Webサーバの起動によるDocker基本操作

Nginxを用いたWebサーバコンテナをDockerコマンド一つで起動し、Dockerの基本的な操作感を体験する。

複雑な設定を行わず、まずはDockerによってアプリケーションが簡単に立ち上がることを理解することを目的としている。

## Work2 マニフェストファイルを用いたNginxサーバの構築とカスタマイズ

Dockerfile や docker-compose.yml といったマニフェストファイルを利用することで、Nginxコンテナを構築する。

設定ファイルやコンテンツを定義することにより、カスタマイズ可能なWebサーバ環境を構築する。

## Work3 PostgreSQLコンテナの構築と永続化によるデータベース基盤の整備

PostgreSQLを用いたデータベースコンテナを起動し、データの永続化や外部からの接続が可能な状態を構築する。

Webシステムと連携可能なバックエンドデータベース基盤の理解と、その運用の基礎を学ぶ。

## Work4 BIツールのコンテナ化によるデータ可視化基盤の構築

BIツール(Apache Superset)をDockerで起動し、前段で構築したPostgreSQLと連携させてデータを可視化する。

システム全体としての流れを体験することで、Dockerを用いた実用的なシステム構成への理解を深める。

# ローカルにコードをクローンする

```
git clone https://github.com/halchil/Netsugen-Docker.git
```


# 情報源

本リポジトリおよびワークショップに関連する技術情報は、以下の信頼性の高い公式情報源を参照している。

学習の補足や更なる理解の深化にご活用ください。

OSSを使う際は、常にリリースノートや最新情報をキャッチしておくことが重要となる。


## 公式ドキュメント

[Docker公式ドキュメント](https://docs.docker.com/)

Dockerの基本概念、コマンドリファレンス、Dockerfileの構文、Composeファイルの記述方法などが網羅されている。

[日本OSS推進フォーラム](https://www.ossforum.jp/)

日本のOSS技術の普及・推進に関する情報がまとめられており、Dockerや関連技術の実践事例も掲載されている。

[Cloud Native Computing Foundation(CNCF)](https://www.cncf.io/)

コンテナ、Kubernetes、クラウドネイティブ技術の標準化・エコシステム形成を推進する国際団体。

[PostgreSQL公式ドキュメント](https://www.postgresql.org/docs/)

PostgreSQLの導入、設定、SQL構文、チューニングなど、幅広いトピックが記載されている。

[Nginx公式ドキュメント](https://nginx.org/en/docs/)

Nginxのインストール、設定、モジュール、パフォーマンス最適化などの情報が網羅されている。


[Apache Superset 公式ドキュメント](https://superset.apache.org/docs/)

BIツールであるApache Supersetの導入方法、設定、ダッシュボード作成、データソース接続方法などが詳しく掲載されている。



## OSS・コンテナ・クラウドネイティブ関連

[CNCF Blog](https://www.cncf.io/blog/)

[Docker Blog](https://www.docker.com/blog/)

[GitHub Trending](https://github.com/trending)


## セキュリティ・脆弱性情報

[JVN（Japan Vulnerability Notes）](https://jvn.jp/)
日本語で確認できる公式脆弱性情報。
DockerやOSS関連のCVEも確認可能。

[CVE Details](https://www.cvedetails.com/)
全世界の脆弱性データベース。DockerやSuperset、PostgreSQLなどの脆弱性検索にも対応。


<!--
## 技術全般
Medium（英語）：https://medium.com/
→ DevOps、クラウド、コンテナ関連の英語記事が豊富（特に「The New Stack」「Towards Data Science」などの系列）。

dev.to（英語）：https://dev.to/
→ 海外エンジニアの知見・最新事例が多く集まる開発者コミュニティ。


# その他

# OSSバージョンの管理
OSSを使う際は、常にリリースノートや最新情報をキャッチしておくことが重要となる。
今回はApache SupersetとPostgreSQLの活用に伴い、関連ドキュメントを貼る。


[Apache Superset GitHub](https://github.com/apache/superset)
[PostgreSQL Github](https://github.com/postgres/postgres)


## 設計思想の起源
PostgreSQLの論文

# docker build create

```

[コンテナ停止コマンド]
docker-compose -f superset-dev.yaml down

[イメージビルドコマンド]
docker-compose -f superset-dev.yaml build

[コンテナランコマンド]
docker-compose -f superset-dev.yaml up -d
```

# ソースコード読解編
Apache Supersetは、Pythonベースで記載されている。
レベルアップに伴い、OSSのコード読解・コントリビュートも視野に入れていきたいので、軽くソースを読んでみる。



# CLIでDBの接続確認
Apache Supersetコンテナにて、きちんとPostgreSQLコンテナにへ接続が通るか簡単にテストする。

```
[実行コマンド]
bash -c "exec 3<>/dev/tcp/superset_db/5432; echo OK"

[結果]
OK
```

試しにポートを変えてみた。

```
[実行コマンド]
bash -c "exec 3<>/dev/tcp/superset_db/5431; echo OK"

[結果]
bash: connect: Connection refused
bash: line 1: /dev/tcp/superset_db/5431: Connection refused
OK
```
ポートをわざと異なるものに設定した場合、接続が通らなくなった。ここからも、ポート指定が正しく行われていたことが分かった。


-->