# 事件信息

查询一个事件详细信息。

!!! info "http"
    GET https://www.microiot.top/server/events/{id}

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称 | 类型   | 必选 | 描述   |
| ---- | ------ | ---- | ------ |
| id   | string | 是   | 事件id |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [Event](#event) | 事件信息 |



## 示例

### 请求URI示例

``` HTTP
GET https://www.microiot.top/server/events/5dd134fb0e8e3d00019e569d
```

### 响应示例

``` JSON
{
    "id": "5dd134fb0e8e3d00019e569d",
    "notifyObject": {
        "type": "device",
        "id": "5dd12fa20e8e3d0001714667",
        "name": "001",
        "connected": true,
        "deviceType": {
            "id": "5dd12f7c0e8e3d0001714666",
            "name": "冰箱",
            "description": "物联网冰箱",
            "domain": {
                "type": "domain",
                "id": "5dd12f000e8e3d0001714665",
                "name": "admin",
                "string": "admin",
                "fullString": "admin"
            },
            "attDefinition": {
                "温度": {
                    "dataType": {
                        "type": "Decimal"
                    },
                    "optional": false,
                    "description": "冰箱内温度",
                    "get": true,
                    "set": true,
                    "report": true
                }
            },
            "staticAttDefinition": {
                "型号": {
                    "dataType": {
                        "type": "String",
                        "min": 0,
                        "max": 1024
                    },
                    "optional": false,
                    "description": "冰箱型号"
                }
            },
            "alarmTypes": null,
            "actionTypes": null
        },
        "attributes": {
            "型号": {
                "type": "String",
                "value": "a1",
                "string": "a1"
            }
        },
        "location": {
            "type": "domain",
            "id": "5dd12f000e8e3d0001714665",
            "name": "admin",
            "string": "admin",
            "fullString": "admin"
        },
        "domain": {
            "type": "domain",
            "id": "5dd12f000e8e3d0001714665",
            "name": "admin",
            "string": "admin",
            "fullString": "admin"
        },
        "deviceAccount": {
            "id": null,
            "username": "f9bb68f2-a2ae-47a2-a85e-552b51ffd4c6",
            "status": "enable",
            "email": null,
            "roles": [
                "DEVICE"
            ],
            "isSystem": false,
            "isArea": false,
            "isDevice": true,
            "area": null
        },
        "string": "001冰箱",
        "fullString": "admin001冰箱"
    },
    "domain": {
        "type": "domain",
        "id": "5dd12f000e8e3d0001714665",
        "name": "admin",
        "string": "admin",
        "fullString": "admin"
    },
    "reportTime": "2019-11-17 19:54:34",
    "receiveTime": "2019-11-17 19:54:35",
    "attribute": "温度",
    "value": {
        "type": "Decimal",
        "value": 2.3,
        "string": "2.3"
    }
}
```

## 类型定义

### Event

事件详细信息。

| 名称         | 类型                                            | 描述                 |
| ------------ | ----------------------------------------------- | -------------------- |
| id           | string                                          | 事件id               |
| notifyObject | [Device](../device/adddevice.md#device)         | 上报事件的设备       |
| attribute    | string                                          | 属性名称             |
| value        | [DataValue](../datatype/datavalue.md#datavalue) | 属性值               |
| reportTime   | date                                            | 事件上报时间         |
| receiveTime  | date                                            | 平台接收到事件的时间 |
| domain       | [Domain](../domain/adddomain.md#domain)         | 事件所属领域         |

