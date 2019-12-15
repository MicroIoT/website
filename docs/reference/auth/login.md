# 用户登录

注册成功MicroIoT平台用户后，使用账号密码登录平台获取token凭证。

!!! info "http"
    POST https://www.microiot.top/server/login


## 访问控制

| 访问用户角色 | 是否需要认证 |
| :----------- | :----------- |
| 任何人       | 否           |

## 请求体

| 名称     | 类型   | 必选 | 描述       |
| -------- | ------ | ---- | ---------- |
| username | string | 是   | 用户名     |
| password | string | 是   | 用户密码   |
| domain   | string | 否   | 登录的领域 |

## 响应

| 状态 | 类型            | 描述      |
| ---- | --------------- | --------- |
| 200  | [Token](#token) | 认证token |

## 示例

### 响应示例

``` JSON
{
    "token": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsInNjb3BlcyI6ImNhb3hpbnl1QGdtYWlsLmNvbSIsImlzcyI6Im1pY3JvaW90IiwiaWF0IjoxNTc0NzI1ODkyLCJleHAiOjE1NzQ3Mjk0OTJ9.k1NitW8dkljfyAb2bk4UmQPtvpHa8ng2pMwmtdOgAikXZGWO8t6sPvHHMOWAlXH0bsxZAGhqnuUWoQpDKheN6g",
    "refreshToken": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsInNjb3BlcyI6ImNhb3hpbnl1QGdtYWlsLmNvbSIsImlzcyI6Im1pY3JvaW90IiwianRpIjoiNWQwMjNiYzUtZGNlZS00Mzg1LWFiYmEtMjg3N2RiYzI4NWNmIiwiaWF0IjoxNTc0NzI1ODkyLCJleHAiOjE1NzQ4MTIyOTJ9.oK3twEzX9JhtbKbssdhb1ENiNvXmrpfzevBvRxNAJudX5ZBUl0wL8LW2CkRzGLP0L2mVzlehM8O1kV_Vz7WH0A"
}
```

## 类型定义

### Token

token详细信息。

| 名称     | 类型   | 描述   |
| -------- | ------ | ------ |
| token    | string | token |
| refreshToken | string | 刷新token |
