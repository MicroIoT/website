# 添加用户

添加一个新的MicroIoT平台用户。

``` HTTP
POST https://www.microiot.top/server/user
```
## 访问控制

| 访问用户角色 | 是否需要认证                                 |
| :----------- | :------------------------------------------- |
| 系统管理员   | 是，使用Bearer Token认证，具体信息见登录授权 |


## 请求体

| 名称     | 类型          | 必选 | 描述                                                   |
| -------- | ------------- | ---- | ------------------------------------------------------ |
| username | string        | 是   | 用户名                                                 |
| password | string        | 是   | 用户密码                                               |
| email    | string        | 是   | 用户电子邮件                                           |
| role     | [Role](#role) | 是   | 用户角色                                               |
| area     | string[]      | 否   | 如果用户角色为区域管理员，area是用户所负责区域的id列表 |



## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [User](#user) | 成功添加的用户 |



## 示例

### 请求体示例

``` JSON
{
  "username": "caoxinyu",
  "password": "password",
  "email": "caoxinyu@gmail.com",
  ”role”: “AREA”,
  "area": [
    "59dc8f8c16bbb720b82f67e3",
    "59e4798cc915d92da081f1f9"
  ]
}
```

### 响应示例

角色为系统管理员的用户信息：

``` JSON
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
```

角色为区域管理员的用户信息：

``` JSON
{
    "id": "5cab0eafddd50a20164a4cfa",
    "username": "caoxinyu",
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
            "id": "5caa9b7dddd50a20164a4cd8",
            "name": "001",
            "parent": null,
            "siteType": {
                "id": "5caa9b4cddd50a20164a4cd7",
                "name": "共享单车",
                "description": "企业在校园、地铁站点、公交站点、居民区等提供自行车单车共享服务。",
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
            "string": "001共享单车"
        }
    ]
}
```

## 类型定义

### User

MicroIoT注册用户详细信息。

| 名称     | 类型   | 描述   |
| -------- | ------ | ------ |
| id       | string | 用户id |
| username | string | 用户名 |
| password | string | 用户密码       |
| status | [Status](#status) | 用户当前状态 |
| email | string | 用户电子邮件 |
| roles | [Role](#role)[] | 用户角色 |
| area | [Domain](../domain/adddomain.md#domain), [Site](../site/addsite.md#site), [Device](../device/adddevice.md#device)[] | 区域管理员负责的区域列表，区域可以是领域，场地或者设备 |
| isSystem | boolean | 是否是系统管理员 |
| isArea | boolean | 是否是区域管理员 |
| isDevice | boolean | 是否是设备 |

### Role

MicroIoT注册用户角色。

| 名称   | 类型   | 描述       |
| ------ | ------ | ---------- |
| SYSTEM | string | 系统管理员 |
| AREA   | string | 区域管理员 |
| DEVICE | string | 设备       |

### Status

MicroIoT注册用户状态。

| 名称    | 类型   | 描述     |
| ------- | ------ | -------- |
| pending | string | 待定状态 |
| enable  | string | 启用状态 |



