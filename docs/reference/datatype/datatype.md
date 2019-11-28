## DataType

DataType描述数据类型元信息。MicroIoT当前支持十种数据类型，每种数据类型有不同的描述信息，详细介绍参见入门指南中[核心概念](../../start/concept.md#_2)。下面列出每种数据类型的详细信息。

### IntType

整数数据类型：

| 名称 | 类型   | 描述 |
| ---- | ------ | ---- |
| type | string | Int  |

#### 示例

``` JSON
{
    "type": "Int"
}
```

### DecimalType

小数数据类型：

| 名称 | 类型   | 描述    |
| ---- | ------ | ------- |
| type | string | Decimal |

#### 示例

``` JSON
{
    "type": "Decimal"
}
```

### LocationType

经纬度位置数据类型：

| 名称 | 类型   | 描述     |
| ---- | ------ | -------- |
| type | string | Location |

#### 示例

``` JSON
{
    "type": "Location"
}
```

### BoolType

布尔数据类型：

| 名称 | 类型   | 描述     |
| ---- | ------ | -------- |
| type | string | Bool |

#### 示例


``` JSON
{
    "type": "Bool"
}
```

### StringType

字符串数据类型：

| 名称 | 类型   | 描述           |
| ---- | ------ | -------------- |
| type | string | String         |
| min  | int    | 字符串最小长度 |
| max  | int    | 字符串最大长度 |

#### 示例

``` JSON
{
    "type": "String",
    "min": 10,
    "max": 256
}
```

### EnumType

枚举数据类型：

| 名称     | 类型     | 描述         |
| -------- | -------- | ------------ |
| type     | string   | Enum         |
| enumType | string[] | 允许的枚举值 |

#### 示例

``` JSON
{
    "type": "Enum",
    "enumType": [
        "红色",
        "黄色",
        "绿色",
        "紫色",
        "蓝色"
    ]
}
```

### DateType

日期时间数据类型：

| 名称   | 类型   | 描述         |
| ------ | ------ | ------------ |
| type   | string | DateTime     |
| format | string | 日期时间格式 |

#### 示例

``` JSON
{
    "type": "DateTime",
    "format": "yyyy-MM-dd HH:mm:ss"
}
```

### ArrayType

数组数据类型：

| 名称     | 类型         | 描述               |
| -------- | ------------ | ------------------ |
| type     | string       | Array              |
| dataType | [DataType]() | 数组内部的数据类型 |

#### 示例

整数数组

``` JSON
{
    "type": "Array",
    "dataType": {
        "type": "Int"
    }
}
```

字符串数组

``` JSON
{
    "type": "Array",
    "dataType": {
        "type": "String",
        "min": 10,
        "max": 20
    }
}
```

### StructType

结构数据类型：

| 名称     | 类型                                                         | 描述               |
| -------- | ------------------------------------------------------------ | ------------------ |
| type     | string                                                       | Struct             |
| attTypes | map(string, [AttributeType](../../devicetype/adddevicetype#attributetype)) | 结构内部的属性类型 |

#### 示例

``` JSON
{
    "type": "Struct",
    "attTypes": {
        "probableCause": {
            "dataType": {
                "type": "String",
                "min": 10,
                "max": 256
            },
            "optional": true,
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
}
```

### ChoiceType

任意数据类型：

| 名称     | 类型                                   | 描述                                      |
| -------- | -------------------------------------- | ----------------------------------------- |
| type     | string                                 | Choice                                    |
| attTypes | map(string, [StructType](#structtype)) | 可选的数据类型，key值是可选的数据类型名称 |

#### 示例

下面的例子是一个Choice数据类型，它可以是Int，Decimal，Location，String四种数据类型中任意一种。

``` JSON
{
    "type": "Choice",
    "attTypes": {
        "c1": {
            "dataType": {
                "type": "Struct",
                "attTypes": {
                    "a": {
                        "dataType": {
                            "type": "Int"
                        },
                        "optional": true,
                        "description": "属性1"
                    }
                }
            },
            "optional": false,
            "description": "Int数据类型"
        },
        "c2": {
            "dataType": {
                "type": "Struct",
                "attTypes": {
                    "a": {
                        "dataType": {
                            "type": "Decimal"
                        },
                        "optional": true,
                        "description": "属性1"
                    }
                }
            },
            "optional": false,
            "description": "Decimal数据类型"
        },
        "c3": {
            "dataType": {
                "type": "Struct",
                "attTypes": {
                    "a": {
                        "dataType": {
                            "type": "Location"
                        },
                        "optional": true,
                        "description": "属性1"
                    }
                }
            },
            "optional": false,
            "description": "Location数据类型"
        },
        "c4": {
            "dataType": {
                "type": "Struct",
                "attTypes": {
                    "a": {
                        "dataType": {
                            "type": "String",
                            "min": 10,
                            "max": 256
                        },
                        "optional": true,
                        "description": "属性1"
                    }
                }
            },
            "optional": false,
            "description": "String数据类型"
        }
    }
}
```

