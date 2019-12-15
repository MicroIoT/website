# 增加设备

向一个设备组中增加一个设备。

!!! info "http"
    POST https://www.microiot.top/server/devicegroups/group/{groupId}/device/{deviceId}

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称     | 类型   | 必选 | 描述     |
| -------- | ------ | ---- | -------- |
| groupId  | string | 是   | 设备组id |
| deviceId | string | 是   | 设备id   |

## 响应

| 状态 | 类型                                         | 描述                 |
| ---- | -------------------------------------------- | -------------------- |
| 200  | [DeviceGroup](adddevicegroup.md#devicegroup) | 成功增加设备的设备组 |



## 示例

### 请求URI示例

!!! info "http"
    GET https://www.microiot.top/server/devicetypes/5dd756190e8e3d000147b973/device/5dd78d800e8e3d000147b976


### 响应示例

参见[设备组信息](adddevicegroup.md#_7)。
