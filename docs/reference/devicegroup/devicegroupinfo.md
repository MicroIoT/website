# 设备组信息

查询一个设备组详细信息。

``` HTTP
GET https://www.microiot.top/server/devicegroups/{id}
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见登录授权 |

## 请求参数

| 名称 | 类型   | 必选 | 描述     |
| ---- | ------ | ---- | -------- |
| id   | string | 是   | 设备组id |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [DeviceGroup](adddevicegroup.md#devicegroup) | 设备组信息 |



## 示例

### 请求URI示例

``` HTTP
GET https://www.microiot.top/server/devicegroups/5dd756190e8e3d000147b973
```

### 响应示例

参见[设备组信息](adddevicegroup.md#_7)。

