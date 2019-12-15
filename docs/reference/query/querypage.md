# 按查询条件查询对象列表页

根据查询条件查询对象列表页。返回结果必须在当前领域范围内。

!!! info "http"
    GET https://www.microiot.top/server/{queryObject}/query/page?filter={filter}&sort={sort}

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称        | 类型                                  | 必选 | 描述                 |
| ----------- | ------------------------------------- | ---- | -------------------- |
| queryObject | [QueryObject](queryid.md#queryobject) | 是   | 查询对象             |
| filter      | string                                | 否   | 查询过滤条件         |
| sort        | string                                | 否   | 查询排序             |
| pageNumber  | int                                   | 否   | 当前页数，缺省为0    |
| pageSize    | int                                   | 否   | 每页显示数，缺省为10 |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [Device](../device/adddevice.md#device)或[Site](../site/addsite.md#site)或[Event](../event/addevent.md#event)或[Alarm](../alarm/addalarm.md#alarm)或[DeviceGroup](../devicegroup/adddevicegroup.md#devicegroup) [Page](../datatype/page.md#page) | 查询对象信息页 |



## 示例

### 请求URI示例

!!! info "http"
    GET https://www.microiot.top/server/devices/query/page?filter={ name: "001" }&sort={ connected: 1 }&pageSize=5



