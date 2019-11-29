# 添加领域

添加一个新的领域。

``` HTTP
POST https://www.microiot.top/server/domains
```
## 访问控制

| 访问用户角色 | 是否需要认证                                 |
| :----------- | :------------------------------------------- |
| 系统管理员   | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |


## 请求体

| 名称 | 类型   | 必选 | 描述     |
| ---- | ------ | ---- | -------- |
| name | string | 是   | 领域名称 |



## 响应

| 状态 | 类型              | 描述           |
| ---- | ----------------- | -------------- |
| 200  | [Domain](#domain) | 成功添加的领域 |



## 示例

### 请求体示例

``` JSON
{
    "name": "meters"
}
```

### 响应示例

``` JSON
{
    "type": "domain",
    "id": "5ddbbc430e8e3d0001f60ed9",
    "name": "meters",
    "string": "meters",
    "fullString": "meters"
}
```

## 类型定义

### Domain

领域详细信息。

| 名称     | 类型   | 描述   |
| -------- | ------ | ------ |
| id       | string | 领域id |
| name | string | 领域名称   |
| string | string | 领域描述名称，与名称相同 |
| fullString | string | 领域全名称，与名称相同 |

