# 用户信息

查询MicroIoT平台用户信息。

``` HTTP
GET https://www.microiot.top/server/users/{username}
```
## 访问控制

| 访问用户角色 | 是否需要认证                                 |
| :----------- | :------------------------------------------- |
| 系统管理员   | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称     | 类型   | 必选 | 描述         |
| -------- | ------ | ---- | ------------ |
| username | string | 是   | 用户名       |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [User](adduser.md#user) | 用户信息 |



## 示例

### 请求URI示例

``` HTTP
GET https://www.microiot.top/server/users/caoxinyu@gmail.com
```

### 响应示例

参见[用户信息](adduser.md#_7)。

