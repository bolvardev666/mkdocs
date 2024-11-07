# 路由


```python
from fastapi import APIRouter


route = APIRouter()

@route.post("/add_user", tags=["user"])
async def add_user(user_obj: UserAll):               #UserAll对象来自数据模型
    result = await user_service.add_user(user_obj)  #具体业务实现
    return {"message": result}
```