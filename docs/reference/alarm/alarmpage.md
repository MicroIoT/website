# 告警列表页

按页查询告警列表。查询结果只返回当前领域内符合查询条件的告警。

``` HTTP
GET https://www.microiot.top/server/events?deviceId={deviceId}&attribute={attribute}&reportFrom={reportFrom}&reportTo={reportTo}&receiveFrom={receiveFrom}&receiveTo={receiveTo}&currentPage={currentPage}&numPerPage={numPerPage}
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见登录授权 |

## 请求参数

| 名称           | 类型   | 必选 | 描述                                                |
| -------------- | ------ | ---- | --------------------------------------------------- |
| notifyObjectId | string | 否   | 告警对象id                                          |
| alarmType      | string | 否   | 告警类型                                            |
| reportFrom     | date   | 否   | 查询上报开始时间，日期格式为yyyy-MM-dd HH:mm:ss     |
| reportTo       | date   | 否   | 查询上报结束时间，日期格式为yyyy-MM-dd HH:mm:ss     |
| receiveFrom    | date   | 否   | 查询平台接收开始时间，日期格式为yyyy-MM-dd HH:mm:ss |
| receiveTo      | date   | 否   | 查询平台接收结束时间，日期格式为yyyy-MM-dd HH:mm:ss |
| currentPage    | int    | 否   | 当前页数，缺省为0                                   |
| numPerPage     | int    | 否   | 每页显示数，缺省为20                                |

## 请求体

无

## 响应

| 状态 | 类型                                                        | 描述       |
| ---- | ----------------------------------------------------------- | ---------- |
| 200  | [Alarm](addalarm.md#alarm) [Page](../../datatype/page#page) | 告警列表页 |



## 示例

### 请求URI示例

查询第一页事件列表页，告警对象id为5dd12fa20e8e3d0001714667：

``` HTTP
GET https://www.microiot.top/server/alarms?notifyObjectId=5ddb2fbe0e8e3d0001f60ec9
```

### 响应示例

``` mmJSON
{
    "content": [
        {
            "id": "5ddc8fe20e8e3d0001f60eee",
            "notifyObject": {
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
            "reportTime": "2019-11-26 10:37:22",
            "receiveTime": "2019-11-26 10:37:22",
            "alarmType": "AttributeChangedAlarm"
        },
        {
            "id": "5ddc8fbb0e8e3d0001f60eec",
            "notifyObject": {
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
            "reportTime": "2019-11-26 10:36:43",
            "receiveTime": "2019-11-26 10:36:43",
            "alarmType": "AttributeChangedAlarm"
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
