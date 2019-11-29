# 按查询条件查询distinct对象列表

根据查询条件查询不同的对象列表。返回结果必须在当前领域范围内。

``` HTTP
GET https://www.microiot.top/server/{queryObject}/query/distinct?filter={filter}&sort={sort}&field={field}&returnClass={returnClass}
```
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
| field       | string                                | 是   | 查询不同的对象的字段 |
| returnClass | [QueryObject](queryid.md#queryobject) | 是   | 查询返回的不同的对象 |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [Device](../device/adddevice.md#device)或[Site](../site/addsite.md#site)或[Event](../event/addevent.md#event)或[Alarm](../alarm/addalarm.md#alarm)或[DeviceGroup](../devicegroup/adddevicegroup.md#devicegroup)[] | 查询对象信息数组 |



## 示例

### 请求URI示例

查询上线设备按deviceType字段查询的不同的DeviceType对象。

``` HTTP
GET https://www.microiot.top/server/devices/query/distinct?filter={connected: true}&field=deviceType&returnClass=devicetypes
```


