# 场地列表页

按页查询场地列表。查询结果只返回当前领域内符合查询条件的场地。

``` HTTP
GET https://www.microiot.top/server/sites?locationId={locationId}&siteTypeId={siteTypeId}&name={name}&currentPage={currentPage}&numPerPage={numPerPage}
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称        | 类型   | 必选 | 描述                 |
| ----------- | ------ | ---- | -------------------- |
| locationId  | string | 否   | 父场地id             |
| siteTypeId  | string | 否   | 场地类型id           |
| name        | string | 否   | 对场地名称正则查询   |
| currentPage | int    | 否   | 当前页数，缺省为0    |
| numPerPage  | int    | 否   | 每页显示数，缺省为20 |

## 请求体

无

## 响应

| 状态 | 类型                                                     | 描述       |
| ---- | -------------------------------------------------------- | ---------- |
| 200  | [Site](addsite.md#site) [Page](../../datatype/page#page) | 场地列表页 |



## 示例

### 请求URI示例

查询第一页场地列表页，场地名称带有1：

``` HTTP
GET https://www.microiot.top/server/sites?name=1
```

### 响应示例

``` mmJSON
{
    "content": [
        {
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
    "totalElements": 1,
    "last": true,
    "sort": {
        "sorted": true,
        "unsorted": false,
        "empty": false
    },
    "numberOfElements": 1,
    "first": true,
    "size": 20,
    "number": 0,
    "empty": false
}
```
