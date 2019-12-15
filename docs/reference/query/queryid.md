# 按id查询对象

根据对象的id查询一个对象的详细信息。返回结果必须在当前领域范围内。

!!! info "http"
    GET https://www.microiot.top/server/{queryObject}/query/id/{id}

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称        | 类型                        | 必选 | 描述     |
| ----------- | --------------------------- | ---- | -------- |
| queryObject | [QueryObject](#queryobject) | 是   | 查询对象 |
| id          | string                      | 是   | 对象id   |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [Device](../device/adddevice.md#device)或[Site](../site/addsite.md#site)或[Event](../event/addevent.md#event)或[Alarm](../alarm/addalarm.md#alarm)或[DeviceGroup](../devicegroup/adddevicegroup.md#devicegroup) | 查询对象信息 |



## 示例

### 请求URI示例

!!! info "http"
    GET https://www.microiot.top/server/devices/query/id/5ddb17b00e8e3d0001f60ec7




## 类型定义

### QueryObject

统一查询可以查询的对象。

| 名称         | 类型   | 描述       |
| ------------ | ------ | ---------- |
| devices      | string | 查询设备   |
| sites        | string | 查询场地   |
| devicegroups | string | 查询设备组 |
| events       | string | 查询事件   |
| alarms       | string | 查询告警   |
