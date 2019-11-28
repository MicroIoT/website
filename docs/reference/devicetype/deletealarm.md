# 移除告警类型

从一个设备类型中删除一个告警类型。

``` HTTP
DELETE https://www.microiot.top/server/devicetypes/{id}/alarmtype/{alarmtype}
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见登录授权 |

## 请求参数

| 名称      | 类型   | 必选 | 描述             |
| --------- | ------ | ---- | ---------------- |
| id        | string | 是   | 设备类型id       |
| alarmtype | string | 是   | 要删除的告警类型 |

## 响应

| 状态 | 类型                      | 描述                       |
| ---- | ------------------------- | -------------------------- |
| 200  | [DeviceType](#devicetype) | 成功删除告警类型的设备类型 |

## 示例

### 请求URI示例

删除告警类型：StatusChangedAlarm

``` HTTP
GET https://www.microiot.top/server/devicetypes/5dd756190e8e3d000147b973/alarmtype/StatusChangedAlarm
```

### 响应示例

参见[设备类型信息](adddevicetype.md#_7)。
