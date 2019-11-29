# 设备列表页

按页查询设备列表。查询结果只返回当前领域内符合查询条件的设备。

``` HTTP
GET https://www.microiot.top/server/devices?locationId={locationId}&deviceTypeId={deviceTypeId}&name={name}&currentPage={currentPage}&numPerPage={numPerPage}
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称         | 类型   | 必选 | 描述                 |
| ------------ | ------ | ---- | -------------------- |
| locationId   | string | 否   | 父场地id             |
| deviceTypeId | string | 否   | 设备类型id           |
| name         | string | 否   | 对设备名称正则查询   |
| currentPage  | int    | 否   | 当前页数，缺省为0    |
| numPerPage   | int    | 否   | 每页显示数，缺省为20 |

## 请求体

无

## 响应

| 状态 | 类型                                                         | 描述       |
| ---- | ------------------------------------------------------------ | ---------- |
| 200  | [Device](adddevice.md#device) [Page](../../datatype/page#page) | 设备列表页 |



## 示例

### 请求URI示例

查询第一页设备列表页，设备类型id为5dd67dba0e8e3d00012613ff：

``` HTTP
GET https://www.microiot.top/server/devices?deviceTypeId=5dd67dba0e8e3d00012613ff
```

### 响应示例

``` mmJSON
{
    "content": [
        {
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
                    "value": "L101000001",
                    "string": "L101000001"
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
            "id": "5dd6806c0e8e3d0001261400",
            "name": "001",
            "connected": true,
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
                    "value": "1234567890",
                    "string": "1234567890"
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
                "username": "b4f8ca2d-fb05-4c6a-908a-a5cb8b06304c",
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
            "fullString": "admin001智能车锁"
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
    "totalElements": 2,
    "last": true,
    "sort": {
        "sorted": true,
        "unsorted": false,
        "empty": false
    },
    "numberOfElements": 2,
    "first": true,
    "size": 20,
    "number": 0,
    "empty": false
}
```
