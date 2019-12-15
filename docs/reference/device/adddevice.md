# 注册设备

注册一个新的设备。

!!! info "http"
    POST https://www.microiot.top/server/devices


添加场地之前必须要确定当前工作的领域。系统管理员和区域管理员都可以注册设备，但是区域管理员只能在自己负责的区域注册设备。

命名一个设备有三种方式：

1. 名称。每个设备都有一个名称，名称只有在确定设备的父场地，以及设备的类型的情况下，才可以定位一个设备。
2. 描述名称。设备名称和设备类型组成的名称是描述名称。
3. 全名称。设备的全名称是设备所处场地的全名称加上设备的描述名称，设备的全名称可以在整个平台内唯一确定一个设备。

例如北京小学一号教学楼一年级一班教室内部署一台新风机，这台设备名称为001，设备类型为新风机，它的描述名称是001新风机，全名称是*领域名称*北京小学一号教学楼一年级一班教室001新风机。

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |


## 请求体

| 名称       | 类型                                                         | 必选 | 描述                                         |
| ---------- | ------------------------------------------------------------ | ---- | -------------------------------------------- |
| name       | string                                                       | 是   | 设备名称                                     |
| locationId | string                                                       | 是   | 父场地id，父场地可以是场地，也可以是领域     |
| deviceType | string                                                       | 是   | 设备类型名称                                 |
| attInfos   | map(string, [AttValueInfo](../datatype/valueinfo.md#attvalueinfo)) | 否   | 设备静态属性值，key为属性名称，value为属性值 |



## 响应

| 状态 | 类型              | 描述           |
| ---- | ----------------- | -------------- |
| 200  | [Device](#device) | 成功注册的设备 |



## 示例

### 请求体示例

``` JSON
{
    "name": "001",
    "deviceType": "智能车锁",
    "locationId": "5ddb2fbe0e8e3d0001f60ec9",
    "attInfos": {
        "model": {
            "value": "L101000001"
        }
    }
}
```

### 响应示例

``` JSON
{
    "type": "device",
    "id": "5ddb808e0e8e3d0001f60ed0",
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
        "password": "86772601",
        "id": null,
        "username": "801bfe6d-861a-4c3d-a3be-d7a7690503e6",
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
}
```

## 类型定义

### Device

设备详细信息。

| 名称     | 类型   | 描述   |
| -------- | ------ | ------ |
| id       | string | 设备id |
| name | string | 设备名称                                       |
| location | [Domain](../domain/adddomain.md#domain)或[Site](../site/addsite.md#site) | 父场地 |
| deviceType | [DeviceType](../devicetype/adddevicetype.md#devicetype) | 设备类型 |
| attributes | map(string, [DataValue](../datatype/datavalue.md#datavalue)) | 设备属性值 |
| deviceAccount | [User](../user/adduser.md#user) | 设备账号 |
| domain | [Domain](../domain/adddomain.md#domain) | 场地所属领域 |
| string | string | 设备描述名称 |
| fullString | string | 设备全名称 |

