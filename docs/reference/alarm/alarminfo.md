# 告警信息

查询一个告警详细信息。

!!! info "http"
    GET https://www.microiot.top/server/alarms/{id}

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称 | 类型   | 必选 | 描述   |
| ---- | ------ | ---- | ------ |
| id   | string | 是   | 告警id |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [Alarm](addalarm.md#alarm) | 告警信息 |



## 示例

### 请求URI示例

!!! info "http"
    GET https://www.microiot.top/server/alarms/5dd134fb0e8e3d00019e569d


### 响应示例

参见[告警信息](addalarm.md#_7)。
