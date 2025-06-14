# コンテナを立ち上げても500エラー

```
[実行コマンド]
docker logs

[結果]
AttributeError: 'NoneType' object has no attribute 'is_active'
2025-05-07 05:38:36,851:INFO:werkzeug:192.168.56.1 - - [07/May/2025 05:38:36] "GET /superset/welcome/ HTTP/1.1" 500 -
```

このエラーは、user が None になっている（つまり、認証されたユーザーが存在しない）ときに発生

ユーザを作成すればよかった。

```
コマンド
docker exec -it superset bash

コマンド
root@0ffcae668956:/app# superset fab create-admin
/usr/local/lib/python3.10/site-packages/flask_limiter/extension.py:333: UserWarning: Using the in-memory storage for tracking rate limits as no storage was explicitly specified. This is not recommended for production use. See: https://flask-limiter.readthedocs.io#configuring-a-storage-backend for documentation about configuring the storage backend.
  warnings.warn(
2025-05-07 05:39:51,668:INFO:superset.utils.screenshots:No PIL installation found
2025-05-07 05:39:52,086:INFO:superset.utils.pdf:No PIL installation found
Username [admin]: 
User first name [admin]: 
User last name [user]: 
Email [admin@fab.org]: 
Password: 
Repeat for confirmation: 
Recognized Database Authentications.
Admin User admin created.

```