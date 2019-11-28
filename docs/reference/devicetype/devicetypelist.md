# 设备类型列表

查询设备类型列表。查询结果只返回当前领域内符合查询条件的设备类型。

``` HTTP
GET https://www.microiot.top/server/devicetypes/list
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见登录授权 |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [DeviceType](adddevicetype.md#devicetype)[] | 设备类型数组 |



## 示例

### 响应示例

``` JSON
[
    {
        "id": "5dd9e19d0e8e3d000147b987",
        "name": "test2",
        "description": "测试",
        "domain": {
            "type": "domain",
            "id": "5dd12f000e8e3d0001714665",
            "name": "admin",
            "string": "admin",
            "fullString": "admin"
        },
        "attDefinition": {
            "date": {
                "dataType": {
                    "type": "DateTime",
                    "format": "yyyy-MM-dd HH:mm:ss"
                },
                "optional": false,
                "description": "日期",
                "get": true,
                "set": true,
                "report": true
            }
        },
        "staticAttDefinition": null,
        "alarmTypes": null,
        "actionTypes": null
    },
    {
        "id": "5dd9f0780e8e3d000147b98c",
        "name": "test1",
        "description": "测试",
        "domain": {
            "type": "domain",
            "id": "5dd12f000e8e3d0001714665",
            "name": "admin",
            "string": "admin",
            "fullString": "admin"
        },
        "attDefinition": {
            "struct": {
                "dataType": {
                    "type": "Struct",
                    "attTypes": {
                        "probableCause": {
                            "dataType": {
                                "type": "String",
                                "min": 0,
                                "max": 1024
                            },
                            "optional": false,
                            "description": "可能原因"
                        },
                        "perceivedSeverity": {
                            "dataType": {
                                "type": "Enum",
                                "enumType": [
                                    "红色",
                                    "黄色",
                                    "绿色",
                                    "紫色",
                                    "蓝色"
                                ]
                            },
                            "optional": false,
                            "description": "严重程度"
                        }
                    }
                },
                "optional": false,
                "description": "结构",
                "get": true,
                "set": true,
                "report": true
            },
            "array int": {
                "dataType": {
                    "type": "Array",
                    "dataType": {
                        "type": "Int"
                    }
                },
                "optional": false,
                "description": "整数数组",
                "get": true,
                "set": true,
                "report": true
            },
            "array string": {
                "dataType": {
                    "type": "Array",
                    "dataType": {
                        "type": "String",
                        "min": 0,
                        "max": 1024
                    }
                },
                "optional": false,
                "description": "字符串数组",
                "get": true,
                "set": true,
                "report": true
            },
            "choice": {
                "dataType": {
                    "type": "Choice",
                    "attTypes": {
                        "c3": {
                            "dataType": {
                                "type": "Struct",
                                "attTypes": {
                                    "a": {
                                        "dataType": {
                                            "type": "Location"
                                        },
                                        "optional": false,
                                        "description": "属性"
                                    }
                                }
                            },
                            "optional": false,
                            "description": "位置类型"
                        },
                        "c4": {
                            "dataType": {
                                "type": "Struct",
                                "attTypes": {
                                    "a": {
                                        "dataType": {
                                            "type": "String",
                                            "min": 0,
                                            "max": 1024
                                        },
                                        "optional": false,
                                        "description": "属性"
                                    }
                                }
                            },
                            "optional": false,
                            "description": "字符串类型"
                        },
                        "c1": {
                            "dataType": {
                                "type": "Struct",
                                "attTypes": {
                                    "a": {
                                        "dataType": {
                                            "type": "Int"
                                        },
                                        "optional": false,
                                        "description": "属性1"
                                    }
                                }
                            },
                            "optional": false,
                            "description": "整数类型"
                        },
                        "c2": {
                            "dataType": {
                                "type": "Struct",
                                "attTypes": {
                                    "a": {
                                        "dataType": {
                                            "type": "Decimal"
                                        },
                                        "optional": false,
                                        "description": "属性1"
                                    }
                                }
                            },
                            "optional": false,
                            "description": "小数类型"
                        }
                    }
                },
                "optional": false,
                "description": "任意类型",
                "get": true,
                "set": true,
                "report": true
            }
        },
        "staticAttDefinition": null,
        "alarmTypes": null,
        "actionTypes": null
    }
]
```
