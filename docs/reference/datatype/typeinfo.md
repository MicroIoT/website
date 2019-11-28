## AttTypeInfo

属性类型定义是用于定义属性元信息的数据类型。详细介绍参见入门指南中[核心概念](../../start/concept.md#_2)。

| 名称          | 类型                  | 必选 | 描述                                                         |
| ------------- | --------------------- | ---- | ------------------------------------------------------------ |
| name          | string                | 是   | 名称                                                         |
| description   | string                | 否   | 描述                                                         |
| dataType      | [DataType](#datatype) | 是   | 数据类型                                                     |
| optional      | boolean               | 是   | 是否必须                                                     |
| dataTypeInfos | map(string, string)   | 否   | 数据类型附加信息。如果数据类型是String，附加信息是字符串的最小长度和最大长度，对应的key值是string.min，string.max。如果数据类型是Enum，附加信息是枚举类型的可选值，key值是enum.value，可选值之间由;分割。如果数据类型是DateTime，附加信息是日期时间的格式，key值是date.format。如果数据类型是Array，附加信息是数组中的数据类型，key值是array.type，以及这种数据类型定义的附加信息。在定义设备类型时，有一类特殊的附加信息定义设备类型属性是否可读取、可设置、可上报，对应的key值分别是：attribute.get，attribute.set，attribute.report |
| additional    | [AttTypeInfo]()[]     | 否   | 如果数据类型是Struct或Choice，则需要在additional中定义Struct或Choice内部的属性。 |



### ActionTypeInfo

操作类型定义是用于定义操作元信息的数据类型。详细介绍参见入门指南中[核心概念](../../start/concept.md#_2)。

| 名称         | 类型            | 必选 | 描述     |
| ------------ | --------------- | ---- | -------- |
| name         | string          | 是   | 名称     |
| description  | string          | 否   | 描述     |
| requestInfo  | [AttTypeInfo]() | 否   | 请求信息 |
| responseInfo | [AttTypeInfo]() | 否   | 响应信息 |

### DataType

数据类型信息

| 名称     | 类型   | 描述           |
| -------- | ------ | -------------- |
| Int      | string | 整数类型       |
| Decimal  | string | 小数类型       |
| String   | string | 字符串类型     |
| Bool     | string | 布尔类型       |
| Enum     | string | 枚举类型       |
| DateTime | string | 日期时间类型   |
| Location | string | 经纬度位置类型 |
| Array    | string | 数组类型       |
| Struct   | string | 结构类型       |
| Choice   | string | 任意类型       |

### 示例

#### String属性类型定义

``` JSON
{
    "name": "probableCause",
    "description": "可能原因",
    "dataType": "String",
    "dataTypeInfos": {
        "string.min": "10",
        "string.max": "256"
    },
    "optional": true
}
```

#### Enum属性类型定义

``` JSON
{
    "name": "color",
    "description": "颜色",
    "dataType": "Enum",
    "dataTypeInfos": {
        "enum.value": "红色;黄色;绿色;紫色;蓝色"
    },
    "optional": true
}
```

#### String Array属性类型定义

``` JSON
{
    "name": "StringArray",
    "description": "字符串数组数据类型",
    "dataType": "Array",
    "dataTypeInfos": {
        "string.min": "10",
        "string.max": "256",
        "array.type": "String"
    },
    "optional": true
}
```

#### Struct属性类型定义

``` JSON
{
    "name": "struct",
    "description": "结构数据类型",
    "dataType": "Struct",
    "optional": true,
    "additional": [
        {
            "name": "location",
            "description": "经纬度位置",
            "dataType": "Location",
            "optional": false
        },
        {
            "name": "status",
            "description": "状态",
            "dataType": "Bool",
            "optional": false
        },
        {
            "name": "date",
            "dataType": "DateTime",
            "description": "日期",
            "dataTypeInfos": {
                "date.format": "yyyy-MM-dd"
            },
            "optional": true
        }
    ]
}
```

#### Struct Array属性类型定义

``` JSON
{
    "name": "struct array",
    "description": "结构数组数据类型",
    "dataType": "Array",
    "optional": true,
    "dataTypeInfos": {
        "array.type": "Struct"
    },
    "additional": [
        {
            "name": "probableCause",
            "dataType": "String",
            "description": "可能原因",
            "dataTypeInfos": {
                "string.min": "10",
                "string.max": "20"
            },
            "optional": true
        },
        {
            "name": "perceivedSeverity",
            "description": "严重程度",
            "dataType": "Enum",
            "dataTypeInfos": {
                "enum.value": "红色;黄色;绿色;紫色;蓝色"
            },
            "optional": false
        }
    ]
}
```

#### Choice属性类型定义

``` JSON
{
    "name": "choice",
    "description": "任意数据类型",
    "dataType": "Choice",
    "optional": true,
    "additional": [
        {
            "name": "c1",
            "dataType": "Struct",
            "description": "整数数据类型",
            "optional": true,
            "additional": [
                {
                    "name": "a",
                    "dataType": "Int",
                    "description": "属性1",
                    "optional": false
                }
            ]
        },
        {
            "name": "c2",
            "dataType": "Struct",
            "description": "小数数据类型",
            "optional": true,
            "additional": [
                {
                    "name": "a",
                    "dataType": "Decimal",
                    "description": "属性1",
                    "optional": false
                }
            ]
        },
        {
            "name": "c3",
            "dataType": "Struct",
            "description": "位置数据类型",
            "optional": true,
            "additional": [
                {
                    "name": "a",
                    "dataType": "Location",
                    "description": "属性1",
                    "optional": false
                }
            ]
        },
        {
            "name": "c4",
            "dataType": "Struct",
            "description": "字符串数据类型",
            "optional": true,
            "additional": [
                {
                    "name": "a",
                    "dataType": "String",
                    "description": "属性1",
                    "dataTypeInfos": {
                        "string.min": "10",
                        "string.max": "256"
                    },
                    "optional": false
                }
            ]
        }
    ]
}
```

