# 设备类型信息

查询一个设备类型详细信息。

!!! info "http"
    GET https://www.microiot.top/server/devicetypes/{id}

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称 | 类型   | 必选 | 描述       |
| ---- | ------ | ---- | ---------- |
| id   | string | 是   | 设备类型id |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [DeviceType](adddevicetype.md#devicetype) | 设备类型信息 |



## 示例

### 请求URI示例

!!! info "http"
    GET https://www.microiot.top/server/devicetypes/5dd756190e8e3d000147b973


### 响应示例

参见[设备类型信息](adddevicetype.md#_7)。

