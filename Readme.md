# はじめに
6/21 Netsugen Dockerセミナーにご参加いただきありがとうございます。

# ローカルにコードをクローンする。

```
git clone https://github.com/halchil/Netsugen-Docker.git
```

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


