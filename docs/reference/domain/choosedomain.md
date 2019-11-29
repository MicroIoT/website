# 改变当前领域

改变当前工作的领域。

``` HTTP
PATCH https://www.microiot.top/server/domains/{name}
```
## 访问控制

| 访问用户角色             | 是否需要认证                                 |
| :----------------------- | :------------------------------------------- |
| 系统管理员或者区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |


## 请求体

| 名称 | 类型   | 必选 | 描述     |
| ---- | ------ | ---- | -------- |
| name | string | 是   | 领域名称 |



## 响应

| 状态 | 类型            | 描述 |
| ---- | --------------- | ---- |
| 200  | [Token](../auth/login.md#token) | 认证token |



## 示例

### 请求URI示例

``` HTTP
PATCH https://www.microiot.top/server/domains/meters
```

### 响应示例

参见[token示例](../auth/login.md#_6)。


