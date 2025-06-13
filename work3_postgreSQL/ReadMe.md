# DB用のコンテナを起動する
work2では、コンテナにNginxをインストールすることでWebサーバ用として活用した。

ここでは、コンテナにPostgreSQLをインストールすることで、DBとして活用する。


```
[アクセスURL(最後に5050番ポートを指定)]
http://ec2-xxx-xxx-xxx-xxx.ap-northeast-1.compute.amazonaws.com:5050
```

```
docker compose -f docker-compose.yaml up -d
```


# PostgereSQLへデータ追加

PostgreSQLにログイン
```
$ psql -U username -d dbname
```
 DB一覧表示
```
$ \l
```
データベースに接続
```
$ \c データベース名
```
$ テーブル一覧表示
```
$ \dt
```
SELECT文実行
```
$ SELECT * FROM table_name;
```

テーブル作成(そのままコピーして流してOK)
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
[実行コマンド]
superset=# SELECT * FROM sales;

[結果]
id | product_name | quantity | price 
----+--------------+----------+-------
(0 rows)
```
現在、該当のテーブルは空なので、データを挿入する。

```
[実行コマンド]
INSERT INTO sales (product_name, quantity, price) 
VALUES ('Product A', 100, 19.99),
       ('Product B', 50, 29.99);

```

先ほどと同様のselect文にて以下のように結果を確認する。


```
[実行コマンド]
SELECT * FROM sales;

[結果]
 id | product_name | quantity | price 
----+--------------+----------+-------
  1 | Product A    |      100 | 19.99
  2 | Product B    |       50 | 29.99
(2 rows)

```

# UI側で確認

![UI](./img/img1.png)

チャートを作成する。

![chart](./img/chart1.png)

SQL Labからクエリを投げてみる。

![SQL Lab](./img/sql-lab1.png)

ダッシュボードの作成
検証中