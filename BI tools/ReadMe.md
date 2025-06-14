# 事前準備

# 起動済コンテナをクリーンにする

DB情報などが引き継がれないように、コンテナ周りをきれいにする。
```
docker compose -f superset-dev.yaml down --volumes --rmi all
```

起動時も同様に、イメージビルドから行う。

```
docker compose -f superset-dev.yaml up --build
```

# Docker Network作成

以下のコマンドより、`superset-net`ネットワークを作成する。
```
docker network create superset-net
```

# PostgreSQLの接続設定

pgAdminにログイン
左側の「Servers」を右クリックして、「Create」→「Server」を選択する。

以下の情報を入力
General タブ:
Name: 任意の名前（例: Superset Database など）

Connection タブ:
Host name/address: PostgreSQLのコンテナ名（この例では superset_db）

Port: 5432（デフォルト）

Maintenance database: superset

Username: superset（PostgreSQLのユーザー名）

Password: superset（PostgreSQLのパスワード）入力後、接続を保存して完了。

# トラブルシュート

ユーザを作成し、pgadmin起動

```
[実行コマンド]
docker compose  -f pgadmin-dev.yaml up -d

[結果]
WARN[0000] /home/mainte/Netsugen-Docker/dev2/pgadmin-dev.yaml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion 
WARN[0000] networks.default: external.name is deprecated. Please set name and external: true 
[+] Running 6/17
 ⠧ pgadmin [⣿⡀⣿⣿⣿⣿⣿⠀⠀⠀⠀⠀⠀⠀⠀⠀] Pulling                                      7.7s 
   ✔ f18232174bc9 Already exists                                           0.0s 
   ⠋ 1df1dde7c499 Downloading  24.13MB/102.9MB                             4.0s 
   ✔ a382f7466647 Download complete                                        2.1s 
   ✔ 51289cd114c2 Download complete                                        1.0s 
   ✔ 6f5081be338a Download complete                                        2.6s 
   ✔ e35a1a6248a3 Download complete                                        3.4s 
   ✔ 10cbb4977e53 Download complete                                        3.7s 
   ⠋ 6a32f2ccafba Waiting                                                  4.0s 
...
```
# UI接続確認
コンテナが立ち上がり、接続できた

自分のローカルサーバのIPを使って、
`http://192.168.56.129:5050`でアクセス。
UTを表示できた。

# DB登録
完了
アイコンから比較的簡単に設定可能。

# ファイルアップロードしてテーブル作成したい

気象データセット
[Kaggle Dataset](https://www.kaggle.com/datasets/muthuj7/weather-dataset)

