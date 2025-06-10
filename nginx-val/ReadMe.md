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

