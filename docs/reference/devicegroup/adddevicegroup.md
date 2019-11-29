# 添加设备组

添加一个新的设备组。添加设备组之前必须要确定当前工作的领域。

``` HTTP
POST https://www.microiot.top/server/devicegroups
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |


## 请求体

| 名称    | 类型     | 必选 | 描述       |
| ------- | -------- | ---- | ---------- |
| name    | string   | 是   | 设备组名称 |
| devices | string[] | 是   | 设备id数组 |



## 响应

| 状态 | 类型                        | 描述             |
| ---- | --------------------------- | ---------------- |
| 200  | [DeviceGroup](#devicegroup) | 成功添加的设备组 |



## 示例

### 请求体示例

``` JSON
{
	"name":"设备组",
	"devices": [
		"5ddb83fb0e8e3d0001f60ed3",
		"5dda3f6e0e8e3d0001f60eb4"
	]
}
```

### 响应示例

``` JSON
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
```

## 类型定义

### DeviceGroup

设备组详细信息。

| 名称     | 类型   | 描述   |
| -------- | ------ | ------ |
| id       | string | 设备组id |
| name | string | 设备组名称                                         |
| devices | [Device](../device/adddevice.md#device)[] | 设备数组         |
| domain  | [Domain](../domain/adddomain.md#domain)  | 设备类型所属领域 |

