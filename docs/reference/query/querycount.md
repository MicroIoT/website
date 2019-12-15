# 按查询条件查询数量

根据查询条件查询符合条件的对象数量。

!!! info "http"
    GET https://www.microiot.top/server/{queryObject}/query/count?filter={filter}&sort={sort}

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称        | 类型                                  | 必选 | 描述         |
| ----------- | ------------------------------------- | ---- | ------------ |
| queryObject | [QueryObject](queryid.md#queryobject) | 是   | 查询对象     |
| filter      | string                                | 否   | 查询过滤条件 |
| sort        | string                                | 否   | 查询排序     |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | long | 符合查询条件的对象数量 |



## 示例

### 请求URI示例

!!! info "http"
    GET https://www.microiot.top/server/devices/query/count?filter={ name: "001" }&sort={ connected: 1 }



