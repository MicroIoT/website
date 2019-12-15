# 事件列表页

按页查询事件列表。查询结果只返回当前领域内符合查询条件的事件。

!!! info "http"
    GET https://www.microiot.top/server/events?deviceId={deviceId}&attribute={attribute}&reportFrom={reportFrom}&reportTo={reportTo}&receiveFrom={receiveFrom}&receiveTo={receiveTo}&currentPage={currentPage}&numPerPage={numPerPage}

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称        | 类型   | 必选 | 描述                                                |
| ----------- | ------ | ---- | --------------------------------------------------- |
| deviceId    | string | 否   | 设备id                                              |
| attribute   | string | 否   | 设备属性                                            |
| reportFrom  | date   | 否   | 查询上报开始时间，日期格式为yyyy-MM-dd HH:mm:ss     |
| reportTo    | date   | 否   | 查询上报结束时间，日期格式为yyyy-MM-dd HH:mm:ss     |
| receiveFrom | date   | 否   | 查询平台接收开始时间，日期格式为yyyy-MM-dd HH:mm:ss |
| receiveTo   | date   | 否   | 查询平台接收结束时间，日期格式为yyyy-MM-dd HH:mm:ss |
| currentPage | int    | 否   | 当前页数，缺省为0                                   |
| numPerPage  | int    | 否   | 每页显示数，缺省为20                                |

## 请求体

无

## 响应

| 状态 | 类型                                                        | 描述       |
| ---- | ----------------------------------------------------------- | ---------- |
| 200  | [Event](addevent.md#event) [Page](../../datatype/page#page) | 事件列表页 |



## 示例

### 请求URI示例

查询第一页事件列表页，设备id为5dd12fa20e8e3d0001714667：

!!! info "http"
    GET https://www.microiot.top/server/events?deviceId=5dd12fa20e8e3d0001714667


### 响应示例

``` mmJSON
{
    "content": [
        {
            "id": "5dd8f7350e8e3d000147b985",
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
            "reportTime": "2019-11-23 17:09:09",
            "receiveTime": "2019-11-23 17:09:09",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 234.4,
                "string": "234.4"
            }
        },
        {
            "id": "5dd350d00e8e3d00012613ea",
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
            "reportTime": "2019-11-19 10:17:52",
            "receiveTime": "2019-11-19 10:17:52",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 4.5,
                "string": "4.5"
            }
        },
        {
            "id": "5dd350c70e8e3d00012613e9",
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
            "reportTime": "2019-11-19 10:17:43",
            "receiveTime": "2019-11-19 10:17:43",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 3.44,
                "string": "3.44"
            }
        },
        {
            "id": "5dd350c10e8e3d00012613e8",
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
            "reportTime": "2019-11-19 10:17:37",
            "receiveTime": "2019-11-19 10:17:37",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 3.44,
                "string": "3.44"
            }
        },
        {
            "id": "5dd285da0e8e3d00012613e0",
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
            "reportTime": "2019-11-18 19:51:54",
            "receiveTime": "2019-11-18 19:51:54",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 2.345,
                "string": "2.345"
            }
        },
        {
            "id": "5dd2592b0e8e3d000125afaf",
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
            "reportTime": "2019-11-18 16:41:12",
            "receiveTime": "2019-11-18 16:41:15",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 4.5,
                "string": "4.5"
            }
        },
        {
            "id": "5dd24f8e0e8e3d000188b8fc",
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
            "reportTime": "2019-11-18 16:00:13",
            "receiveTime": "2019-11-18 16:00:14",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 4.5,
                "string": "4.5"
            }
        },
        {
            "id": "5dd233420e8e3d00019465a9",
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
            "reportTime": "2019-11-18 13:59:29",
            "receiveTime": "2019-11-18 13:59:30",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 4.5,
                "string": "4.5"
            }
        },
        {
            "id": "5dd2202f0e8e3d00019465a8",
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
            "reportTime": "2019-11-18 12:38:06",
            "receiveTime": "2019-11-18 12:38:07",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 4.5,
                "string": "4.5"
            }
        },
        {
            "id": "5dd1fcce0e8e3d00019465a1",
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
            "reportTime": "2019-11-18 10:07:08",
            "receiveTime": "2019-11-18 10:07:10",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 4.5,
                "string": "4.5"
            }
        },
        {
            "id": "5dd1fcc20e8e3d00019465a0",
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
            "reportTime": "2019-11-18 10:06:56",
            "receiveTime": "2019-11-18 10:06:58",
            "attribute": "温度",
            "value": {
                "type": "Decimal",
                "value": 3.4,
                "string": "3.4"
            }
        },
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
    ],
    "pageable": {
        "sort": {
            "sorted": true,
            "unsorted": false,
            "empty": false
        },
        "pageSize": 20,
        "pageNumber": 0,
        "offset": 0,
        "unpaged": false,
        "paged": true
    },
    "totalPages": 1,
    "totalElements": 12,
    "last": true,
    "sort": {
        "sorted": true,
        "unsorted": false,
        "empty": false
    },
    "numberOfElements": 12,
    "first": true,
    "size": 20,
    "number": 0,
    "empty": false
}
```
