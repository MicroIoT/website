# 领域信息

查询一个领域详细信息。可以按领域的id查询，也可以按照领域的名称查询。

``` HTTP
GET https://www.microiot.top/server/domains/id/{id}
```

``` HTTP
GET https://www.microiot.top/server/domains/name/{name}
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称 | 类型   | 必选 | 描述     |
| ---- | ------ | ---- | -------- |
| id   | string | 是   | 领域id   |
| name | string | 是   | 领域名称 |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [Domain](adddomain.md#domain) | 领域信息 |



## 示例

### 请求URI示例

``` HTTP
GET https://www.microiot.top/server/domains/id/5dd245fd0e8e3d00019465bc
```

### 响应示例

参见[领域信息](adddomain.md#_7)。

