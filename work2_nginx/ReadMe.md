```
docker compose -f docker-compose.yaml up -d
```

```
http://url → index.htmlが表示
http://url/test → nginx.confのルーティング表示
http://url/secret → 403 deny
```

```
docker compose -f docker-compose.yaml down
```