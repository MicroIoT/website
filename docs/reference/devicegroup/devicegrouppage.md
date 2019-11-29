# 设备组列表页

按页查询设备组列表。查询结果只返回当前领域内符合查询条件的设备组。查询设备组列表页与查询设备组列表类似，只是一个返回的是设备组翻页数据，一个返回的是设备组数组数据，用户可以按照需要选择使用。

``` HTTP
GET https://www.microiot.top/server/devicegroups/page?currentPage={currentPage}&numPerPage={numPerPage}
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称        | 类型 | 必选 | 描述                 |
| ----------- | ---- | ---- | -------------------- |
| currentPage | int  | 否   | 当前页数，缺省为0    |
| numPerPage  | int  | 否   | 每页显示数，缺省为20 |

## 请求体

无

## 响应

| 状态 | 类型                                                         | 描述         |
| ---- | ------------------------------------------------------------ | ------------ |
| 200  | [DeviceGroup](adddevicegroup.md#devicegroup) [Page](../../datatype/page#page) | 设备组列表页 |



## 示例

### 请求URI示例

查询第一页设备组列表页，每页查询两个设备组：

``` HTTP
GET https://www.microiot.top/server/devicegroups/page?numPerPage=2
```

### 响应示例

``` JSON
{
    "content": [
        {
            "id": "5ddba87f0e8e3d0001f60ed8",
            "name": "设备组1",
            "devices": [
                {
                    "type": "device",
                    "id": "5ddb83fb0e8e3d0001f60ed3",
                    "name": "001",
                    "connected": false,
                    "deviceType": {
                        "id": "5dd67dba0e8e3d00012613ff",
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
                    },
                    "attributes": {
                        "model": {
                            "type": "String",
                            "value": "L101000002",
                            "string": "L101000002"
                        }
                    },
                    "location": {
                        "type": "site",
                        "id": "5ddb2fbe0e8e3d0001f60ec9",
                        "name": "001",
                        "location": {
                            "type": "domain",
                            "id": "5dd12f000e8e3d0001714665",
                            "name": "admin",
                            "string": "admin",
                            "fullString": "admin"
                        },
                        "siteType": {
                            "id": "5ddb17b00e8e3d0001f60ec7",
                            "name": "共享单车",
                            "description": "企业在校园、地铁站点、公交站点、居民区、商业区、公共服务区等提供自行车单车共享服务。",
                            "domain": {
                                "type": "domain",
                                "id": "5dd12f000e8e3d0001714665",
                                "name": "admin",
                                "string": "admin",
                                "fullString": "admin"
                            },
                            "attDefinition": {
                                "city": {
                                    "dataType": {
                                        "type": "String",
                                        "min": 0,
                                        "max": 255
                                    },
                                    "optional": true,
                                    "description": "共享单车所属城市"
                                },
                                "model": {
                                    "dataType": {
                                        "type": "String",
                                        "min": 0,
                                        "max": 255
                                    },
                                    "optional": true,
                                    "description": "共享单车的型号"
                                },
                                "sn": {
                                    "dataType": {
                                        "type": "String",
                                        "min": 0,
                                        "max": 255
                                    },
                                    "optional": true,
                                    "description": "共享单车的序列号"
                                }
                            }
                        },
                        "attributes": {
                            "city": {
                                "type": "String",
                                "value": "北京",
                                "string": "北京"
                            },
                            "model": {
                                "type": "String",
                                "value": "b001",
                                "string": "b001"
                            },
                            "sn": {
                                "type": "String",
                                "value": "0001",
                                "string": "0001"
                            }
                        },
                        "domain": {
                            "type": "domain",
                            "id": "5dd12f000e8e3d0001714665",
                            "name": "admin",
                            "string": "admin",
                            "fullString": "admin"
                        },
                        "string": "001共享单车",
                        "fullString": "admin001共享单车"
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
                        "username": "6efde294-6199-4628-82a1-c397a0eb896d",
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
                    "string": "001智能车锁",
                    "fullString": "admin001共享单车001智能车锁"
                },
                {
                    "type": "device",
                    "id": "5dd12fa20e8e3d0001714667",
                    "name": "001",
                    "connected": false,
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
                }
            ],
            "domain": {
                "type": "domain",
                "id": "5dd12f000e8e3d0001714665",
                "name": "admin",
                "string": "admin",
                "fullString": "admin"
            }
        },
        {
            "id": "5ddb9ee10e8e3d0001f60ed6",
            "name": "设备组",
            "devices": [
                {
                    "type": "device",
                    "id": "5ddb83fb0e8e3d0001f60ed3",
                    "name": "001",
                    "connected": false,
                    "deviceType": {
                        "id": "5dd67dba0e8e3d00012613ff",
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
                    },
                    "attributes": {
                        "model": {
                            "type": "String",
                            "value": "L101000002",
                            "string": "L101000002"
                        }
                    },
                    "location": {
                        "type": "site",
                        "id": "5ddb2fbe0e8e3d0001f60ec9",
                        "name": "001",
                        "location": {
                            "type": "domain",
                            "id": "5dd12f000e8e3d0001714665",
                            "name": "admin",
                            "string": "admin",
                            "fullString": "admin"
                        },
                        "siteType": {
                            "id": "5ddb17b00e8e3d0001f60ec7",
                            "name": "共享单车",
                            "description": "企业在校园、地铁站点、公交站点、居民区、商业区、公共服务区等提供自行车单车共享服务。",
                            "domain": {
                                "type": "domain",
                                "id": "5dd12f000e8e3d0001714665",
                                "name": "admin",
                                "string": "admin",
                                "fullString": "admin"
                            },
                            "attDefinition": {
                                "city": {
                                    "dataType": {
                                        "type": "String",
                                        "min": 0,
                                        "max": 255
                                    },
                                    "optional": true,
                                    "description": "共享单车所属城市"
                                },
                                "model": {
                                    "dataType": {
                                        "type": "String",
                                        "min": 0,
                                        "max": 255
                                    },
                                    "optional": true,
                                    "description": "共享单车的型号"
                                },
                                "sn": {
                                    "dataType": {
                                        "type": "String",
                                        "min": 0,
                                        "max": 255
                                    },
                                    "optional": true,
                                    "description": "共享单车的序列号"
                                }
                            }
                        },
                        "attributes": {
                            "city": {
                                "type": "String",
                                "value": "北京",
                                "string": "北京"
                            },
                            "model": {
                                "type": "String",
                                "value": "b001",
                                "string": "b001"
                            },
                            "sn": {
                                "type": "String",
                                "value": "0001",
                                "string": "0001"
                            }
                        },
                        "domain": {
                            "type": "domain",
                            "id": "5dd12f000e8e3d0001714665",
                            "name": "admin",
                            "string": "admin",
                            "fullString": "admin"
                        },
                        "string": "001共享单车",
                        "fullString": "admin001共享单车"
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
                        "username": "6efde294-6199-4628-82a1-c397a0eb896d",
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
                    "string": "001智能车锁",
                    "fullString": "admin001共享单车001智能车锁"
                },
                {
                    "type": "device",
                    "id": "5dda3f6e0e8e3d0001f60eb4",
                    "name": "001",
                    "connected": false,
                    "deviceType": {
                        "id": "5dd756190e8e3d000147b973",
                        "name": "智能车锁1",
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
                            },
                            "status": {
                                "dataType": {
                                    "type": "Enum",
                                    "enumType": [
                                        "pending",
                                        "enable"
                                    ]
                                },
                                "optional": false,
                                "description": "共享单车当前状态",
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
                            },
                            "StatusChangedAlarm": {
                                "dataType": {
                                    "type": "Enum",
                                    "enumType": [
                                        "pending",
                                        "enable"
                                    ]
                                },
                                "optional": true,
                                "description": "状态改变告警"
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
                    },
                    "attributes": {
                        "model": {
                            "type": "String",
                            "value": "s-123456789",
                            "string": "s-123456789"
                        }
                    },
                    "location": {
                        "type": "site",
                        "id": "5ddb2fbe0e8e3d0001f60ec9",
                        "name": "001",
                        "location": {
                            "type": "domain",
                            "id": "5dd12f000e8e3d0001714665",
                            "name": "admin",
                            "string": "admin",
                            "fullString": "admin"
                        },
                        "siteType": {
                            "id": "5ddb17b00e8e3d0001f60ec7",
                            "name": "共享单车",
                            "description": "企业在校园、地铁站点、公交站点、居民区、商业区、公共服务区等提供自行车单车共享服务。",
                            "domain": {
                                "type": "domain",
                                "id": "5dd12f000e8e3d0001714665",
                                "name": "admin",
                                "string": "admin",
                                "fullString": "admin"
                            },
                            "attDefinition": {
                                "city": {
                                    "dataType": {
                                        "type": "String",
                                        "min": 0,
                                        "max": 255
                                    },
                                    "optional": true,
                                    "description": "共享单车所属城市"
                                },
                                "model": {
                                    "dataType": {
                                        "type": "String",
                                        "min": 0,
                                        "max": 255
                                    },
                                    "optional": true,
                                    "description": "共享单车的型号"
                                },
                                "sn": {
                                    "dataType": {
                                        "type": "String",
                                        "min": 0,
                                        "max": 255
                                    },
                                    "optional": true,
                                    "description": "共享单车的序列号"
                                }
                            }
                        },
                        "attributes": {
                            "city": {
                                "type": "String",
                                "value": "北京",
                                "string": "北京"
                            },
                            "model": {
                                "type": "String",
                                "value": "b001",
                                "string": "b001"
                            },
                            "sn": {
                                "type": "String",
                                "value": "0001",
                                "string": "0001"
                            }
                        },
                        "domain": {
                            "type": "domain",
                            "id": "5dd12f000e8e3d0001714665",
                            "name": "admin",
                            "string": "admin",
                            "fullString": "admin"
                        },
                        "string": "001共享单车",
                        "fullString": "admin001共享单车"
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
                        "username": "1c02fd5a-0189-4c28-a671-782861adbc68",
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
                    "string": "001智能车锁1",
                    "fullString": "admin001共享单车001智能车锁1"
                }
            ],
            "domain": {
                "type": "domain",
                "id": "5dd12f000e8e3d0001714665",
                "name": "admin",
                "string": "admin",
                "fullString": "admin"
            }
        }
    ],
    "pageable": {
        "sort": {
            "sorted": true,
            "unsorted": false,
            "empty": false
        },
        "pageSize": 2,
        "pageNumber": 0,
        "offset": 0,
        "unpaged": false,
        "paged": true
    },
    "totalPages": 1,
    "totalElements": 2,
    "last": true,
    "sort": {
        "sorted": true,
        "unsorted": false,
        "empty": false
    },
    "numberOfElements": 2,
    "first": true,
    "size": 2,
    "number": 0,
    "empty": false
}
```
