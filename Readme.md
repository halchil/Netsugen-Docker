# はじめに
Netsugenセミナー

[システム構成図]
ココにシステム構成図を記載

# 目的
docekrの理解
ネットワーク
ボリュームなど

# バージョンの管理
[Apache Superset GitHub](https://github.com/apache/superset)
[PostgreSQL Github]()

# Officialサイト

# 設計思想の起源
PostgreSQLの論文

# docker build create

```
docker-compose -f superset-dev.yaml build
docker-compose -f superset-dev.yaml down
docker-compose -f superset-dev.yaml up -d
```


# ソースコード読解編

# 初期パスワード作成

```
docker exec -it superset superset fab create-admin
/usr/local/lib/python3.10/site-packages/flask_limiter/extension.py:333: UserWarning: Using the in-memory storage for tracking rate limits as no storage was explicitly specified. This is not recommended for production use. See: https://flask-limiter.readthedocs.io#configuring-a-storage-backend for documentation about configuring the storage backend.
  warnings.warn(
2025-05-07 01:44:00,620:INFO:superset.utils.screenshots:No PIL installation found
2025-05-07 01:44:01,032:INFO:superset.utils.pdf:No PIL installation found
Username [admin]: 
User first name [admin]: 
User last name [user]: 
Email [admin@fab.org]: 
Password: 
Repeat for confirmation: 
Recognized Database Authentications.
Admin User admin created.
```

# UI側からDBの接続確認

```
bash -c "exec 3<>/dev/tcp/superset_db/5432; echo OK"
OK
```

試しにポートを変えた

```
bash -c "exec 3<>/dev/tcp/superset_db/5431; echo OK"
bash: connect: Connection refused
bash: line 1: /dev/tcp/superset_db/5431: Connection refused
OK
```

# PostgereSQLへデータ追加

PostgreSQLにログイン
```
psql -U username -d dbname
```
 DB一覧表示
```
\l
```
データベースに接続
```
\c データベース名
```

 テーブル一覧表示
```
\dt
```
SELECT文実行
```
SELECT * FROM table_name;
```

テーブル作成
```
CREATE TABLE sales (
    id SERIAL PRIMARY KEY,
    product_name VARCHAR(100),
    quantity INT,
    price DECIMAL
);

```

確認
```
SELECT * FROM table_name;
                      ^
superset=# SELECT * FROM sales;
 id | product_name | quantity | price 
----+--------------+----------+-------
(0 rows)
```
データ挿入

```
INSERT INTO sales (product_name, quantity, price) 
VALUES ('Product A', 100, 19.99),
       ('Product B', 50, 29.99);


```

確認

```
SELECT * FROM sales;
 id | product_name | quantity | price 
----+--------------+----------+-------
  1 | Product A    |      100 | 19.99
  2 | Product B    |       50 | 29.99
(2 rows)

```

UI側で確認

![aaa](./img/img1.png)

# チャートの作成

![chart](./img/chart1.png)

# SQL Labからクエリを投げる

![SQL Lab](./img/sql-lab1.png)

# ダッシュボードの作成

