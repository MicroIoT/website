# 增加操作类型

向一个设备类型中添加一个新的操作类型。

``` HTTP
POST https://www.microiot.top/server/devicetypes/{id}/actiontype
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见登录授权 |

## 请求参数

| 名称 | 类型   | 必选 | 描述       |
| ---- | ------ | ---- | ---------- |
| id   | string | 是   | 设备类型id |

## 请求体

| 名称 | 类型                                                         | 必选 | 描述             |
| ---- | ------------------------------------------------------------ | ---- | ---------------- |
| info | [ActionTypeInfo](../../datatype/typeinfo/#actiontypeinfo) | 是   | 设备操作类型信息 |



## 响应

| 状态 | 类型                      | 描述                       |
| ---- | ------------------------- | -------------------------- |
| 200  | [DeviceType](#devicetype) | 成功添加动态属性的设备类型 |



## 示例

### 请求URI示例

``` HTTP
GET https://www.microiot.top/server/devicetypes/5dd756190e8e3d000147b973/actiontype
```

### 请求体示例

``` JSON
{
    "name": "getHistory",
    "description": "获取共享单车某段时间骑行数据历史记录",
    "requestInfo": {
        "name": "filter",
        "description": "查询条件",
        "dataType": "Struct",
        "optional": false,
        "additional": [
            {
                "name": "startDate",
                "dataType": "DateTime",
                "description": "查询开始日期",
                "dataTypeInfos": {
                    "date.format": "yyyy-MM-dd"
                },
                "optional": true
            },
            {
                "name": "endDate",
                "dataType": "DateTime",
                "description": "查询结束日期",
                "dataTypeInfos": {
                    "date.format": "yyyy-MM-dd"
                },
                "optional": true
            }
        ]
    },
    "responseInfo": {
        "name": "records",
        "dataType": "Array",
        "description": "骑行记录",
        "dataTypeInfos": {
            "array.type": "Struct"
        },
        "optional": false,
        "additional": [
            {
                "name": "startLocation",
                "description": "骑行开始位置",
                "dataType": "Location",
                "optional": false
            },
            {
                "name": "startTime",
                "description": "骑行开始时间",
                "dataType": "DateTime",
                "dataTypeInfos": {
                    "date.format": "yyyy-MM-dd HH:mm:ss"
                },
                "optional": false
            },
            {
                "name": "endLocation",
                "description": "骑行结束位置",
                "dataType": "Location",
                "optional": false
            },
            {
                "name": "endTime",
                "description": "骑行结束时间",
                "dataType": "DateTime",
                "dataTypeInfos": {
                    "date.format": "yyyy-MM-dd HH:mm:ss"
                },
                "optional": false
            }
        ]
    }
}
```

### 响应示例

参见[设备类型信息](adddevicetype.md#_7)。
