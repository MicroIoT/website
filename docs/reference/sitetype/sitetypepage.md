# 场地类型列表页

按页查询场地类型列表。

!!! info "http"
    GET https://www.microiot.top/server/sitetypes/page?currentPage={currentPage}&numPerPage={numPerPage}

查询结果只返回当前领域内符合查询条件的场地类型。查询场地类型列表页与查询场地类型列表类似，只是一个返回的是场地类型翻页数据，一个返回的是场地类型数组数据，用户可以按照需要选择使用。

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

| 状态 | 类型                                                         | 描述           |
| ---- | ------------------------------------------------------------ | -------------- |
| 200  | [SiteType](addsitetype.md#sitetype) [Page](../../datatype/page#page) | 场地类型列表页 |



## 示例

### 请求URI示例

查询第一页场地类型列表页，每页查询两个场地类型：

!!! info "http"
    GET https://www.microiot.top/server/sitetypes/page?numPerPage=2


### 响应示例

``` mmJSON
{
    "content": [
        {
            "id": "5ddb21cb0e8e3d0001f60ec8",
            "name": "test",
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
                        "format": "yyyy-MM-dd"
                    },
                    "optional": true,
                    "description": "日期"
                },
                "address": {
                    "dataType": {
                        "type": "String",
                        "min": 10,
                        "max": 255
                    },
                    "optional": true,
                    "description": "地址"
                },
                "color": {
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
                    "optional": true,
                    "description": "颜色"
                },
                "status": {
                    "dataType": {
                        "type": "Bool"
                    },
                    "optional": true,
                    "description": "状态"
                }
            }
        },
        {
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
