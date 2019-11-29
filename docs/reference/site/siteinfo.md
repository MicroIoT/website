# 场地信息

查询一个场地详细信息。

``` HTTP
GET https://www.microiot.top/server/sites/{id}
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称 | 类型   | 必选 | 描述   |
| ---- | ------ | ---- | ------ |
| id   | string | 是   | 场地id |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [Site](addsite.md#site) | 场地信息 |



## 示例

### 请求URI示例

``` HTTP
GET https://www.microiot.top/server/sites/5ddb17b00e8e3d0001f60ec7
```

### 响应示例

参见[场地信息](addsite.md#_7)。

