# 添加场地

添加一个新的场地。

``` HTTP
POST https://www.microiot.top/server/sites
```
添加场地之前必须要确定当前工作的领域。系统管理员和区域管理员都可以添加场地，但是区域管理员只能在自己负责的区域添加场地。

命名一个场地有三种方式：

1. 名称。每个场地都有一个名称，名称只有在确定场地的父场地，以及场地的类型的情况下，才可以定位一个场地。
2. 描述名称。在一个领域内，一个场地是通过层级关系，一层一层确定下来。每一层的场地都有场地名称和场地类型，整个从顶到底的场地名称和场地类型组成的名称就是描述名称。
3. 全名称。描述名称只能在一个领域内确定一个场地，全名称在描述名称的基础上加入了领域名称，可以在整个平台内确定一个场地。

例如一个小学叫北京小学，它有一个教学楼，里面有很多教室，一年级一班的教室的名称是一年级一班，场地类型是教室，它的描述名称是北京小学一号教学楼一年级一班教室，而它的全名称要在描述名称前加上领域名。

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见登录授权 |


## 请求体

| 名称       | 类型                                                         | 必选 | 描述                                     |
| ---------- | ------------------------------------------------------------ | ---- | ---------------------------------------- |
| name       | string                                                       | 是   | 场地名称                                 |
| locationId | string                                                       | 是   | 父场地id，父场地可以是场地，也可以是领域 |
| siteType   | string                                                       | 是   | 场地类型名称                             |
| attInfos   | map(string, [AttValueInfo](../datatype/valueinfo.md#attvalueinfo)) | 否   | 场地属性值，key为属性名称，value为属性值 |



## 响应

| 状态 | 类型          | 描述           |
| ---- | ------------- | -------------- |
| 200  | [Site](#site) | 成功添加的场地 |



## 示例

### 请求体示例

``` JSON
{
    "name": "001",
    "siteType": "共享单车",
    "locationId": "5d76ffa42ab79c0001efbc44",
    "attInfos": {
        "city": {
            "value": "北京"
        },
        "model": {
            "value": "b001"
        },
        "sn": {
            "value": "0001"
        }
    }
}
```

### 响应示例

``` JSON
{
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
}
```

## 类型定义

### Site

场地详细信息。

| 名称     | 类型   | 描述   |
| -------- | ------ | ------ |
| id       | string | 场地id |
| name | string | 场地名称                                       |
| location | [Domain](../domain/adddomain.md#domain)或[Site](#site) | 父场地 |
| siteType | [SiteType](../sitetype/addsitetype.md#sitetype) | 场地类型 |
| attributes | map(string, [DataValue](../datatype/datavalue.md#datavalue)) | 场地属性值 |
| domain | [Domain](../domain/adddomain.md#domain) | 场地所属领域 |
| string | string | 场地描述名称 |
| fullString | string | 场地全名称 |

