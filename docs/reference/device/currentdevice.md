# 当前设备信息

查询当前登录设备的详细信息。

!!! info "http"
    GET https://www.microiot.top/server/devices/me

## 访问控制

| 访问用户角色 | 是否需要认证                                 |
| :----------- | :------------------------------------------- |
| 设备         | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [Device](../device/adddevice.md#device) | 设备信息 |



## 示例

### 响应示例

参见[设备信息](../device/adddevice.md#_7)。

