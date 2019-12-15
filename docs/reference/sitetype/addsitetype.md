# 添加场地类型

添加一个新的场地类型。添加场地类型之前必须要确定当前工作的领域。

!!! info "http"
    POST https://www.microiot.top/server/sitetypes

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |


## 请求体

| 名称        | 类型                                                 | 必选 | 描述                 |
| ----------- | ---------------------------------------------------- | ---- | -------------------- |
| name        | string                                               | 是   | 场地类型名称         |
| description | string                                               | 否   | 场地类型描述         |
| dataType    | string                                               | 是   | 数据类型是：Class    |
| optional    | boolean                                              | 是   | 必选                 |
| additional  | [AttTypeInfo](../datatype/typeinfo.md#atttypeinfo)[] | 否   | 场地类型属性定义列表 |



## 响应

| 状态 | 类型                  | 描述               |
| ---- | --------------------- | ------------------ |
| 200  | [SiteType](#sitetype) | 成功添加的场地类型 |



## 示例

### 请求体示例

``` JSON
{
    "name": "共享单车",
    "dataType": "Class",
    "description": "企业在校园、地铁站点、公交站点、居民区、商业区、公共服务区等提供自行车单车共享服务。",
    "optional": true,
    "additional": [
        {
            "name": "city",
            "description": "共享单车所属城市",
            "dataType": "String",
            "dataTypeInfos": {
                "string.min": "0",
                "string.max": "255"
            },
            "optional": true
        },
        {
            "name": "model",
            "description": "共享单车的型号",
            "dataType": "String",
            "dataTypeInfos": {
                "string.min": "0",
                "string.max": "255"
            },
            "optional": true
        },
        {
            "name": "sn",
            "description": "共享单车的序列号",
            "dataType": "String",
            "dataTypeInfos": {
                "string.min": "0",
                "string.max": "255"
            },
            "optional": true
        }
    ]
}
```

### 响应示例

``` JSON
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
```

## 类型定义

### SiteType

场地类型详细信息。

| 名称     | 类型   | 描述   |
| -------- | ------ | ------ |
| id       | string | 场地类型id |
| name | string | 场地类型名称                                       |
| description | string | 场地类型描述 |
| domain | [Domain](../domain/adddomain.md#domain) | 场地类型所属领域 |
| attDefinition | map(string, [AttributeType](../../devicetype/adddevicetype/#attributetype)) | 场地类型属性定义，key为属性名称，value为属性定义 |

