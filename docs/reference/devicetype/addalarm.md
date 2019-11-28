# 增加告警类型

向一个设备类型中添加一个新的告警类型。

``` HTTP
POST https://www.microiot.top/server/devicetypes/{id}/alarmtype
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见登录授权 |

## 请求参数

| 名称 | 类型   | 必选 | 描述       |
| ---- | ------ | ---- | ---------- |
| id   | string | 是   | 设备类型id |

## 请求体

| 名称 | 类型                                                         | 必选 | 描述             |
| ---- | ------------------------------------------------------------ | ---- | ---------------- |
| info | [AttTypeInfo](http://localhost:8000/reference/datatype/typeinfo/#atttypeinfo) | 是   | 设备告警类型信息 |



## 响应

| 状态 | 类型                      | 描述                       |
| ---- | ------------------------- | -------------------------- |
| 200  | [DeviceType](#devicetype) | 成功添加告警类型的设备类型 |



## 示例

### 请求URI示例

``` HTTP
GET https://www.microiot.top/server/devicetypes/5dd756190e8e3d000147b973/alarmtype
```

### 请求体示例

``` JSON
{
    "name": "StatusChangedAlarm",
    "dataType": "Enum",
    "description": "状态改变告警",
    "optional": true,
    "dataTypeInfos": {
        "enum.value": "pending;enable"
    }
}
```

### 响应示例

参见[设备类型信息](adddevicetype.md#_7)。

