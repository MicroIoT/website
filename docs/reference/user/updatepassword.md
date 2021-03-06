# 修改密码

修改当前登录用户的密码。

!!! info "http"
    PATCH https://www.microiot.top/server/users/password

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求体

| 名称     | 类型   | 必选 | 描述     |
| -------- | ------ | ---- | -------- |
| original | string | 是   | 原密码   |
| password | string | 是   | 修改密码 |

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [User](adduser.md#user) | 修改密码成功的用户 |

## 示例

### 请求体示例

``` JSON
{
  "original": "123456",
  "password": "password"
}
```

### 响应示例

参见[用户信息](adduser.md#_7)。
