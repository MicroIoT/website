# 删除领域

删除一个领域。

!!! info "http"
    DELETE https://www.microiot.top/server/domains/{id}

## 访问控制

| 访问用户角色 | 是否需要认证                                 |
| :----------- | :------------------------------------------- |
| 系统管理员   | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称 | 类型   | 必选 | 描述           |
| ---- | ------ | ---- | -------------- |
| id   | string | 是   | 被删除领域的id |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  |  |  |



## 示例

### 请求URI示例

!!! info "http"
    DELETE https://www.microiot.top/server/domains/5dd756190e8e3d000147b973



