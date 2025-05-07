

# psycopg2が無いエラー

```
docker exec -it superset bash
superset@aa24281595b6:/app$ python
Python 3.10.16 (main, Mar 17 2025, 23:56:33) [GCC 12.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import psycopg2
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'psycopg2'
```


```
ログ

File "/app/superset/models/core.py", line 539, in _get_sqla_engine
    return create_engine(sqlalchemy_url, **params)
  File "<string>", line 2, in create_engine
  File "/usr/local/lib/python3.10/site-packages/sqlalchemy/util/deprecations.py", line 375, in warned
    return fn(*args, **kwargs)
  File "/usr/local/lib/python3.10/site-packages/sqlalchemy/engine/create.py", line 544, in create_engine
    dbapi = dialect_cls.dbapi(**dbapi_args)
  File "/usr/local/lib/python3.10/site-packages/sqlalchemy/dialects/postgresql/psycopg2.py", line 811, in dbapi
    import psycopg2
ModuleNotFoundError: No module named 'psycopg2'
2025-05-07 02:13:16,524:INFO:werkzeug:192.168.56.1 - - [07/May/2025 02:13:16] "POST /api/v1/database/validate_parameters/ HTTP/1.1" 500 -
2025-05-07 02:13:45,950:INFO:werkzeug:127.0.0.1 - - [07/May/2025 02:13:45] "GET /health HTTP/1.1" 200 -
2025-05-07 02:14:16,055:INFO:werkzeug:127.0.0.1 - - [07/May/2025 02:14:16] "GET /health HTTP/1.1" 200 -
2025-05-07 02:14:46,191:INFO:werkzeug:127.0.0.1 - - [07/May/2025 02:14:46] "GET /health HTTP/1.1" 200 -
2025-05-07 02:15:16,313:INFO:werkzeug:127.0.0.1 - - [07/May/2025 02:15:16] "GET /health HTTP/1.1" 200 -
```

docker exec -it superset bash

python

import psycopg2

docker-compose -f superset-dev.yaml build

# SupersetコンテナからPostgreSQLコンテナ確認

意味を解析する
bash -c "exec 3<>/dev/tcp/superset_db/5432; echo OK"
