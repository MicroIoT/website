# 改变当前领域

改变当前工作的领域。

``` HTTP
PATCH https://www.microiot.top/server/domains/{name}
```
## 访问控制

| 访问用户角色             | 是否需要认证                                 |
| :----------------------- | :------------------------------------------- |
| 系统管理员或者区域管理员 | 是，使用Bearer Token认证，具体信息见登录授权 |


## 请求体

| 名称 | 类型   | 必选 | 描述     |
| ---- | ------ | ---- | -------- |
| name | string | 是   | 领域名称 |



## 响应

| 状态 | 类型            | 描述 |
| ---- | --------------- | ---- |
| 200  | [Token](#token) | 令牌 |



## 示例

### 请求URI示例

``` HTTP
PATCH https://www.microiot.top/server/domains/meters
```

### 响应示例

``` JSON
{
    "token": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsInNjb3BlcyI6ImNhb3hpbnl1QGdtYWlsLmNvbSIsImlzcyI6Im1pY3JvaW90IiwiaWF0IjoxNTc0NzI1ODkyLCJleHAiOjE1NzQ3Mjk0OTJ9.k1NitW8dkljfyAb2bk4UmQPtvpHa8ng2pMwmtdOgAikXZGWO8t6sPvHHMOWAlXH0bsxZAGhqnuUWoQpDKheN6g",
    "refreshToken": "eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsInNjb3BlcyI6ImNhb3hpbnl1QGdtYWlsLmNvbSIsImlzcyI6Im1pY3JvaW90IiwianRpIjoiNWQwMjNiYzUtZGNlZS00Mzg1LWFiYmEtMjg3N2RiYzI4NWNmIiwiaWF0IjoxNTc0NzI1ODkyLCJleHAiOjE1NzQ4MTIyOTJ9.oK3twEzX9JhtbKbssdhb1ENiNvXmrpfzevBvRxNAJudX5ZBUl0wL8LW2CkRzGLP0L2mVzlehM8O1kV_Vz7WH0A"
}
```

## 类型定义

### Token

令牌详细信息。

| 名称     | 类型   | 描述   |
| -------- | ------ | ------ |
| token    | string | 令牌 |
| refreshToken | string | 刷新令牌 |

