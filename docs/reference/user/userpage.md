# 用户列表页

按页查询MicroIoT平台用户列表。

!!! info "http"
    GET https://www.microiot.top/server/users?currentPage={currentPage}&numPerPage={numPerPage}

## 访问控制

| 访问用户角色 | 是否需要认证                                 |
| :----------- | :------------------------------------------- |
| 系统管理员   | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称        | 类型 | 必选 | 描述                 |
| ----------- | ---- | ---- | -------------------- |
| currentPage | int  | 否   | 当前页数，缺省为0    |
| numPerPage  | int  | 否   | 每页显示数，缺省为20 |

## 请求体

无

## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [User](adduser.md#user) [Page](../../datatype/page#page) | 用户列表页 |



## 示例

### 请求URI示例

查询第二页用户列表示例：

!!! info "http"
    GET https://www.microiot.top/server/users?currentPage=1


### 响应示例

``` JSON
{
    "content": [
        {
            "id": "5dd245fd0e8e3d00019465bd",
            "username": "caoxinyu@test.com",
            "status": "enable",
            "email": "caoxinyu@test.com",
            "roles": [
                "AREA"
            ],
            "isSystem": false,
            "isArea": true,
            "isDevice": false,
            "area": [
                {
                    "id": "5dd245fd0e8e3d00019465bc",
                    "name": "caoxinyu@test.com",
                    "type": "domain",
                    "string": "caoxinyu@test.com",
                    "fullString": "caoxinyu@test.com"
                }
            ]
        },
        {
            "id": "5dd2431c0e8e3d00019465bb",
            "username": "caoxinyu@email.com",
            "status": "enable",
            "email": "caoxinyu@email.com",
            "roles": [
                "AREA"
            ],
            "isSystem": false,
            "isArea": true,
            "isDevice": false,
            "area": [
                {
                    "id": "5dd2431c0e8e3d00019465ba",
                    "name": "caoxinyu@email.com",
                    "type": "domain",
                    "string": "caoxinyu@email.com",
                    "fullString": "caoxinyu@email.com"
                }
            ]
        },
        {
            "id": "5dd242100e8e3d00019465b9",
            "username": "caoxinyu@126.com",
            "status": "enable",
            "email": "caoxinyu@126.com",
            "roles": [
                "AREA"
            ],
            "isSystem": false,
            "isArea": true,
            "isDevice": false,
            "area": [
                {
                    "id": "5dd242100e8e3d00019465b8",
                    "name": "caoxinyu@126.com",
                    "type": "domain",
                    "string": "caoxinyu@126.com",
                    "fullString": "caoxinyu@126.com"
                }
            ]
        },
        {
            "id": "5dd23f440e8e3d00019465b7",
            "username": "caoxinyu@hotmail.com",
            "status": "enable",
            "email": "caoxinyu@hotmail.com",
            "roles": [
                "AREA"
            ],
            "isSystem": false,
            "isArea": true,
            "isDevice": false,
            "area": [
                {
                    "id": "5dd23f440e8e3d00019465b6",
                    "name": "caoxinyu@hotmail.com",
                    "type": "domain",
                    "string": "caoxinyu@hotmail.com",
                    "fullString": "caoxinyu@hotmail.com"
                }
            ]
        },
        {
            "id": "5dd23f080e8e3d00019465b5",
            "username": "caoxinyu@qq.com",
            "status": "enable",
            "email": "caoxinyu@qq.com",
            "roles": [
                "AREA"
            ],
            "isSystem": false,
            "isArea": true,
            "isDevice": false,
            "area": [
                {
                    "id": "5dd23f080e8e3d00019465b4",
                    "name": "caoxinyu@qq.com",
                    "type": "domain",
                    "string": "caoxinyu@qq.com",
                    "fullString": "caoxinyu@qq.com"
                }
            ]
        },
        {
            "id": "5dd23a0b0e8e3d00019465b3",
            "username": "caoxinyu@sina.com",
            "status": "enable",
            "email": "caoxinyu@sina.com",
            "roles": [
                "AREA"
            ],
            "isSystem": false,
            "isArea": true,
            "isDevice": false,
            "area": [
                {
                    "id": "5dd23a0b0e8e3d00019465b2",
                    "name": "caoxinyu@sina.com",
                    "type": "domain",
                    "string": "caoxinyu@sina.com",
                    "fullString": "caoxinyu@sina.com"
                }
            ]
        },
        {
            "id": "5dd238020e8e3d00019465b1",
            "username": "caoxinyu@163.com",
            "status": "enable",
            "email": "caoxinyu@163.com",
            "roles": [
                "AREA"
            ],
            "isSystem": false,
            "isArea": true,
            "isDevice": false,
            "area": [
                {
                    "id": "5dd238020e8e3d00019465b0",
                    "name": "caoxinyu@163.com",
                    "type": "domain",
                    "string": "caoxinyu@163.com",
                    "fullString": "caoxinyu@163.com"
                }
            ]
        },
        {
            "id": "5dd237110e8e3d00019465af",
            "username": "caoxinyu@139.com",
            "status": "enable",
            "email": "caoxinyu@139.com",
            "roles": [
                "AREA"
            ],
            "isSystem": false,
            "isArea": true,
            "isDevice": false,
            "area": [
                {
                    "id": "5dd237110e8e3d00019465ae",
                    "name": "caoxinyu@139.com",
                    "type": "domain",
                    "string": "caoxinyu@139.com",
                    "fullString": "caoxinyu@139.com"
                }
            ]
        },
        {
            "id": "5dd234430e8e3d00019465ad",
            "username": "caoxinyu@msn.com",
            "status": "enable",
            "email": "caoxinyu@msn.com",
            "roles": [
                "AREA"
            ],
            "isSystem": false,
            "isArea": true,
            "isDevice": false,
            "area": [
                {
                    "id": "5dd234430e8e3d00019465ac",
                    "name": "caoxinyu@msn.com",
                    "type": "domain",
                    "string": "caoxinyu@msn.com",
                    "fullString": "caoxinyu@msn.com"
                }
            ]
        },
        {
            "id": "5dd233b80e8e3d00019465ab",
            "username": "caoxinyu@gmail.com",
            "status": "enable",
            "email": "caoxinyu@gmail.com",
            "roles": [
                "AREA"
            ],
            "isSystem": false,
            "isArea": true,
            "isDevice": false,
            "area": [
                {
                    "id": "5dd233b80e8e3d00019465aa",
                    "name": "caoxinyu@gmail.com",
                    "type": "domain",
                    "string": "caoxinyu@gmail.com",
                    "fullString": "caoxinyu@gmail.com"
                }
            ]
        },
        {
            "id": "5dd12e66a82b162186d6907a",
            "username": "admin",
            "status": "enable",
            "email": "caoxinyu@gmail.com",
            "roles": [
                "SYSTEM"
            ],
            "isSystem": true,
            "isArea": false,
            "isDevice": false,
            "area": null
        }
    ],
    "pageable": {
        "sort": {
            "unsorted": false,
            "sorted": true,
            "empty": false
        },
        "pageSize": 20,
        "pageNumber": 0,
        "offset": 0,
        "unpaged": false,
        "paged": true
    },
    "totalPages": 1,
    "totalElements": 11,
    "last": true,
    "sort": {
        "unsorted": false,
        "sorted": true,
        "empty": false
    },
    "first": true,
    "numberOfElements": 11,
    "size": 20,
    "number": 0,
    "empty": false
}
```
