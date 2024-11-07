# pydantic

## pydantic数据模型
允许在使用fastapi路由接收参数时根据数据模型的限制进行接收,很棒
```python
from pydantic import BaseModel,constr


class ChangeUserPassword(User):
    old_password: str
    new_password: constr(min_length=6, max_length=256)

class UserPaging(BaseModel):
    page: int = 1
    limit: int = 50
    order: str = "id"
    sort: str = "desc"

```

## orm-pydantic扩展
使用model直接生成对应的`pydantic`数据模型,`exclud`参数允许生成时排除某些字段
```python
from tortoise.contrib.pydantic import pydantic_model_creator

UserAll = pydantic_model_creator(user_model.User,name="UserAll",exclude=("id",))
```