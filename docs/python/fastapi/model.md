# 数据库ORM模型


```python
from tortoise import models
from tortoise.fields import IntField,CharField


class User(models.Model):
    id = IntField(pk=True,autoincrement=True)
    username = CharField(max_length=50)
    password = CharField(max_length=256)
    email = CharField(max_length=50)
    account = CharField(max_length=50, unique=True)
    sex = CharField(max_length=10, default='未知')

    class Meta:
        table = 'user'      #表名
```