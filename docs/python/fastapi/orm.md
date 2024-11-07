# tortoise-orm 框架
tortoise-orm是一个python `orm`异步框架,使用简单,配置稍微有些麻烦之外没什么缺点

## 1. 在fastapi中的配置

```python

TORTOISE_ORM_CONFIG = {
    'connections': {
        # Dict format for connection
        'default': {
            'engine': 'tortoise.backends.asyncpg',
            'credentials': {
                'host': '127.0.0.1',
                'port': '5432',
                'user': 'bolvar',
                'password': '123.edu',
                'database': 'fastapi',
            }
        },
        # Using a DB_URL string
        # 'default': 'postgres://postgres:qwerty123@localhost:5432/events'
    },
    'apps': {
        'models': {
            'models': ["app.models.user_model"],
            # If no default_connection specified, defaults to 'default'
            'default_connection': 'default',
        }
    },
    "timezone": "Asia/Shanghai",
}
```
> `models`参数需要写到model方法所在的具体py文件,比如我的py模型文件是`user_model.py`
## 2.服务注册
在main.py文件的的app中注册,使用`register_tortoise`方法,注册后无需手动管理
```python
from tortoise.contrib.fastapi import register_tortoise

register_tortoise(
    app,
    config=TORTOISE_ORM_CONFIG,
    generate_schemas=True,  # auto create table ,only devel env using
    add_exception_handlers=True
)
```