# 领域列表

查询当前登录用户的领域列表。

``` HTTP
GET https://www.microiot.top/server/domains/me
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [Domain](adddomain.md#domain)[] | 领域数组 |



## 示例

### 响应示例

``` JSON
[
    {
        "type": "domain",
        "id": "5dd233b80e8e3d00019465aa",
        "name": "caoxinyu@gmail.com",
        "string": "caoxinyu@gmail.com",
        "fullString": "caoxinyu@gmail.com"
    }
]
```

