# 移动设备

把一个设备搬到一个新位置。

!!! info "http"
    PATCH https://www.microiot.top/server/devices/site

系统管理员和区域管理员都可以移动设备，但是区域管理员只能移动自己负责的区域内的设备。移动设备位置后，平台会发出AttributeChangedAlarm告警通知应用端。

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |


## 请求体

| 名称       | 类型   | 必选 | 描述       |
| ---------- | ------ | ---- | ---------- |
| id         | string | 是   | 设备id     |
| locationId | string | 是   | 设备新位置 |


## 响应

| 状态 | 类型                          | 描述           |
| ---- | ----------------------------- | -------------- |
| 200  | [Device](adddevice.md#device) | 成功移动的设备 |



## 示例

### 请求体示例

``` JSON
{
    "id": "5dda3f6e0e8e3d0001f60eb4",
    "locationId": "5ddb2fbe0e8e3d0001f60ec9"
}
```

### 响应示例

参见[设备信息](adddevice.md#_7)。

