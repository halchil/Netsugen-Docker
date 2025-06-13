# 準備運動

## AWSサーバにログイン
Discordにて接続情報配布予定

## Linuxコマンドを試す

ルートディレクトリのファイル一覧を表示する
```
[実行コマンド]
ls /

[結果]
bin  bin.usr-is-merged  boot  dev  etc  home  lib  lib.usr-is-merged  lib64  lost+found  media  mnt  opt  proc  root  run  sbin  sbin.usr-is-merged  snap  srv  sys  tmp  usr  var
```
また、`ll /`と打つと詳細な情報を表示可能。

現在のディレクトリ位置を表示

```
[実行コマンド]
pwd

[結果]
/home/[ユーザ名]
```

現在は、ルートディレクトリ`/`→ホームディレクトリ`home`→ユーザディレクトリ`user名`の位置にいることが確認できる。

次に、ディレクトリ位置を移動する。
```
[一つ上のディレクトリに移動するコマンド]
cd ..

[確認コマンド]
pwd

[結果]
/home
```
ホームディレクトリに移動できていることが分かった。

ホームディレクトリの中身を表示する。
```
[実行コマンド]
ll

[結果]
total 16
drwxr-xr-x  4 root     root     4096 Jun  8 06:22 ./
drwxr-xr-x 22 root     root     4096 Jun 13 12:14 ../
drwxr-x---  4 ubuntu   ubuntu   4096 Jun  8 06:48 ubuntu/
drwxr-x---  6 val-user val-user 4096 Jun 13 12:15 val-user/
```

再度、ユーザディレクトリに移動する。

```
[実行コマンド]
cd ユーザ名

[確認コマンド]
pwd

[結果]
/home/[ユーザ名]

```

試しにファイルを作成(コマンドはコピペ)
```
echo "hello netsugen!" > test.txt
```

ファイルが作成されたかllコマンドで確認し、内容を表示する。

```
[実行コマンド]
cat test.txt

[結果]
hello netsugen!
```

慣れてきたら`tab`キーの予測機能を使って作業効率を上げていく。


# Docker動作確認

ここからはDockerの動作確認を行う。
本日の研修は、既にDockerがインストールされているサーバを用意しているが、自分のサーバで利用する際はインストールから行う必要がある。

[Qiita Docker Install](https://qiita.com/haru_yama/items/487b0248a0694962a05d)

まず、インストールされているDockerのバージョンを確認する。

```
[実行コマンド]
docker version

[結果]
Client: Docker Engine - Community
 Version:           28.2.2
 API version:       1.50
 Go version:        go1.24.3
 Git commit:        e6534b4
 Built:             Fri May 30 12:07:27 2025
 OS/Arch:           linux/amd64
 Context:           default

Server: Docker Engine - Community
 Engine:
  Version:          28.2.2
  API version:      1.50 (minimum version 1.24)
  Go version:       go1.24.3
  Git commit:       45873be
  Built:            Fri May 30 12:07:27 2025
  OS/Arch:          linux/amd64
  Experimental:     false
 containerd:
  Version:          1.7.27
  GitCommit:        05044ec0a9a75232cad458027ca83437aae3f4da
 runc:
  Version:          1.2.5
  GitCommit:        v1.2.5-0-g59923ef
 docker-init:
  Version:          0.19.0
  GitCommit:        de40ad0
```
→出ない人がいたら確認。
次に、helpコマンドで実行可能な処理を確認

```
[実行コマンド]

docker --help
(または、docker -h)

[結果 (重要なコマンド抜粋)]
Common Commands:
  run         Create and run a new container from an image
  exec        Execute a command in a running container
  ps          List containers
  build       Build an image from a Dockerfile
  images      List images
  version     Show the Docker version information
  info        Display system-wide information
```

試しにコンテナを起動する。

```
[実行コマンド]
docker run --rm alpine echo "hello netsugen"

[結果]
Unable to find image 'alpine:latest' locally
latest: Pulling from library/alpine
fe07684b16b8: Pull complete 
Digest: sha256:8a1f59ffb675680d47db6337b49d22281a139e9d709335b492be023728e11715
Status: Downloaded newer image for alpine:latest
hello netsugen
```

alpineOSを積んだコンテナが起動し、`hello netsugen`と言った後に終了した。
(現在は理解できていなくてもOK。)



# Nginxサーバ起動方法

```
[実行コマンド]
docker run --name my-nginx -p 80:80 -d nginx

[結果]
Unable to find image 'nginx:latest' locally
latest: Pulling from library/nginx
61320b01ae5e: Pull complete 
670a101d432b: Extracting [===============================>                   ]  27.98MB/44.15MB
405bd2df85b6: Download complete 
cc80efff8457: Download complete 
2b9310b2ee4b: Download complete 
6c4aa022e8e1: Download complete 
```

```
http://ec2-43-207-212-79.ap-northeast-1.compute.amazonaws.com/
```
httpは80番ポートでのバインドのため、接続できた。

