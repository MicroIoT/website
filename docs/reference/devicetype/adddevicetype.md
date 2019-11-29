# 添加设备类型

添加一个新的设备类型。添加设备类型之前必须要确定当前工作的领域。

``` HTTP
POST https://www.microiot.top/server/devicetypes
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |


## 请求体

| 名称              | 类型                                                       | 必选 | 描述                     |
| ----------------- | ---------------------------------------------------------- | ---- | ------------------------ |
| name              | string                                                     | 是   | 设备类型名称             |
| description       | string                                                     | 否   | 设备类型描述             |
| dataType          | string                                                     | 是   | 数据类型是：Class        |
| optional          | boolean                                                    | 是   | 必选                     |
| additional        | [AttTypeInfo](../datatype/typeinfo.md#atttypeinfo)[]       | 否   | 设备类型动态属性定义列表 |
| staticAttTypeInfo | [AttTypeInfo](../datatype/typeinfo.md#atttypeinfo)[]       | 否   | 设备类型静态属性定义列表 |
| alarmTypeInfos    | [AttTypeInfo](../datatype/typeinfo.md#atttypeinfo)[]       | 否   | 设备类型告警定义列表     |
| actionTypeInfos   | [ActionTypeInfo](../datatype/typeinfo.md#actiontypeinfo)[] | 否   | 设备类型操作定义列表     |



## 响应

| 状态 | 类型                      | 描述               |
| ---- | ------------------------- | ------------------ |
| 200  | [DeviceType](#devicetype) | 成功添加的设备类型 |



## 示例

### 请求体示例

``` JSON
{
    "name": "智能车锁",
    "description": "共享单车智能车锁",
    "dataType": "Class",
    "optional": false,
    "additional": [
        {
            "name": "location",
            "description": "共享单车当前地理位置",
            "dataType": "Location",
            "optional": false,
            "dataTypeInfos": {
                "attribute.get": "true",
                "attribute.set": "false",
                "attribute.report": "true"
            }
        },
        {
            "name": "locked",
            "description": "共享单车当前锁状态",
            "dataType": "Bool",
            "optional": false,
            "dataTypeInfos": {
                "attribute.get": "true",
                "attribute.set": "true",
                "attribute.report": "false"
            }
        }
    ],
    "actionTypeInfos": [
        {
            "name": "getHistory",
            "description": "获取共享单车某段时间骑行数据历史记录",
            "requestInfo": {
                "name": "filter",
                "description": "查询条件",
                "dataType": "Struct",
                "optional": false,
                "additional": [
                    {
                        "name": "startDate",
                        "dataType": "DateTime",
                        "description": "查询开始日期",
                        "dataTypeInfos": {
                            "date.format": "yyyy-MM-dd"
                        },
                        "optional": true
                    },
                    {
                        "name": "endDate",
                        "dataType": "DateTime",
                        "description": "查询结束日期",
                        "dataTypeInfos": {
                            "date.format": "yyyy-MM-dd"
                        },
                        "optional": true
                    }
                ]
            },
            "responseInfo": {
                "name": "records",
                "dataType": "Array",
                "description": "骑行记录",
                "dataTypeInfos": {
                    "array.type": "Struct"
                },
                "optional": false,
                "additional": [
                    {
                        "name": "startLocation",
                        "description": "骑行开始位置",
                        "dataType": "Location",
                        "optional": false
                    },
                    {
                        "name": "startTime",
                        "description": "骑行开始时间",
                        "dataType": "DateTime",
                        "dataTypeInfos": {
                            "date.format": "yyyy-MM-dd HH:mm:ss"
                        },
                        "optional": false
                    },
                    {
                        "name": "endLocation",
                        "description": "骑行结束位置",
                        "dataType": "Location",
                        "optional": false
                    },
                    {
                        "name": "endTime",
                        "description": "骑行结束时间",
                        "dataType": "DateTime",
                        "dataTypeInfos": {
                            "date.format": "yyyy-MM-dd HH:mm:ss"
                        },
                        "optional": false
                    }
                ]
            }
        }
    ],
    "alarmTypeInfos": [
        {
            "name": "StateChangedAlarm",
            "dataType": "Struct",
            "description": "车锁状态改变告警",
            "optional": true,
            "additional": [
                {
                    "name": "location",
                    "description": "车锁状态改变时所处位置",
                    "dataType": "Location",
                    "optional": false
                },
                {
                    "name": "locked",
                    "description": "车锁状态",
                    "dataType": "Bool",
                    "optional": false
                }
            ]
        }
    ],
    "staticAttTypeInfo": [
        {
            "name": "model",
            "dataType": "String",
            "description": "车锁型号",
            "dataTypeInfos": {
                "string.min": "10",
                "string.max": "256"
            },
            "optional": true
        }
    ]
}
```

### 响应示例

``` JSON
{
    "id": "5dd756190e8e3d000147b973",
    "name": "智能车锁",
    "description": "共享单车智能车锁",
    "domain": {
        "type": "domain",
        "id": "5dd12f000e8e3d0001714665",
        "name": "admin",
        "string": "admin",
        "fullString": "admin"
    },
    "attDefinition": {
        "location": {
            "dataType": {
                "type": "Location"
            },
            "optional": false,
            "description": "共享单车当前地理位置",
            "get": true,
            "set": false,
            "report": true
        },
        "locked": {
            "dataType": {
                "type": "Bool"
            },
            "optional": false,
            "description": "共享单车当前锁状态",
            "get": true,
            "set": true,
            "report": false
        }
    },
    "staticAttDefinition": {
        "model": {
            "dataType": {
                "type": "String",
                "min": 10,
                "max": 256
            },
            "optional": true,
            "description": "车锁型号"
        }
    },
    "alarmTypes": {
        "StateChangedAlarm": {
            "dataType": {
                "type": "Struct",
                "attTypes": {
                    "location": {
                        "dataType": {
                            "type": "Location"
                        },
                        "optional": false,
                        "description": "车锁状态改变时所处位置"
                    },
                    "locked": {
                        "dataType": {
                            "type": "Bool"
                        },
                        "optional": false,
                        "description": "车锁状态"
                    }
                }
            },
            "optional": true,
            "description": "车锁状态改变告警"
        }
    },
    "actionTypes": {
        "getHistory": {
            "request": {
                "filter": {
                    "dataType": {
                        "type": "Struct",
                        "attTypes": {
                            "endDate": {
                                "dataType": {
                                    "type": "DateTime",
                                    "format": "yyyy-MM-dd"
                                },
                                "optional": true,
                                "description": "查询结束日期"
                            },
                            "startDate": {
                                "dataType": {
                                    "type": "DateTime",
                                    "format": "yyyy-MM-dd"
                                },
                                "optional": true,
                                "description": "查询开始日期"
                            }
                        }
                    },
                    "optional": false,
                    "description": "查询条件"
                }
            },
            "response": {
                "records": {
                    "dataType": {
                        "type": "Array",
                        "dataType": {
                            "type": "Struct",
                            "attTypes": {
                                "startLocation": {
                                    "dataType": {
                                        "type": "Location"
                                    },
                                    "optional": false,
                                    "description": "骑行开始位置"
                                },
                                "startTime": {
                                    "dataType": {
                                        "type": "DateTime",
                                        "format": "yyyy-MM-dd HH:mm:ss"
                                    },
                                    "optional": false,
                                    "description": "骑行开始时间"
                                },
                                "endTime": {
                                    "dataType": {
                                        "type": "DateTime",
                                        "format": "yyyy-MM-dd HH:mm:ss"
                                    },
                                    "optional": false,
                                    "description": "骑行结束时间"
                                },
                                "endLocation": {
                                    "dataType": {
                                        "type": "Location"
                                    },
                                    "optional": false,
                                    "description": "骑行结束位置"
                                }
                            }
                        }
                    },
                    "optional": false,
                    "description": "骑行记录"
                }
            },
            "description": "获取共享单车某段时间骑行数据历史记录"
        }
    }
}
```

## 类型定义

### DeviceType

设备类型详细信息。

| 名称     | 类型   | 描述   |
| -------- | ------ | ------ |
| id       | string | 设备类型id |
| name | string | 设备类型名称                                         |
| description | string | 设备类型描述 |
| domain | [Domain](../domain/adddomain.md#domain) | 设备类型所属领域 |
| attDefinition | map(string, [DeviceAttributeType](#deviceattributetype)) | 设备类型动态属性定义，key为属性名称，value为动态属性定义 |
| staticAttDefinition | map(string, [AttributeType](#attributetype)) | 设备类型静态属性定义，key为属性名称，value为静态属性定义 |
| alarmTypes | map(string, [AttributeType](#attributetype)) | 设备类型告警定义，key为告警名称，value为告警类型定义 |
| actionTypes | map(string, [ActionType](#actiontype)) | 设备类型操作定义，key为操作名称，value为操作类型定义 |

### AttributeType

属性类型详细信息。

| 名称        | 类型         | 描述     |
| ----------- | ------------ | -------- |
| dataType    | [DataType](../../datatype/datatype#datatype) | 数据类型 |
| optional    | boolean      | 是否必选 |
| description | string       | 描述信息 |

### DeviceAttributeType

设备属性类型详细信息。设备属性类型是在属性类型的基础上增加了属性是否可以读取、可设置、可上报的信息。

| 名称   | 类型    | 描述       |
| ------ | ------- | ---------- |
| get    | boolean | 是否可读取 |
| set    | boolean | 是否可设置 |
| report | boolean | 是否可上报 |
| dataType    | [DataType](../../datatype/datatype#datatype) | 数据类型 |
| optional    | boolean      | 是否必选 |
| description | string       | 描述信息 |

### ActionType

操作类型详细信息。

| 名称        | 类型                                         | 描述             |
| ----------- | -------------------------------------------- | ---------------- |
| description | string                                       | 描述信息         |
| request     | map(string, [AttributeType](#attributetype)) | 操作请求详细信息 |
| response    | map(string, [AttributeType](#attributetype)) | 操作响应详细信息 |

