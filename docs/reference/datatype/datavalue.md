## DataValue

DataValue描述数据值信息。每种数据类型的数据值都有不同的描述方式，下面分别描述各种类型的数据值。

### IntValue

整数值：

| 名称   | 类型   | 描述         |
| ------ | ------ | ------------ |
| type   | string | Int          |
| value  | int    | 整数值       |
| string | string | 整数的字符串 |

#### 示例

``` JSON
{
    "type": "Int",
    "value": 123,
    "string": "123"
}
```

### DecimalValue

小数值：

| 名称   | 类型   | 描述                   |
| ------ | ------ | ---------------------- |
| type   | string | Decimal                |
| value  | double | 双精度浮点数值         |
| string | string | 双精度浮点数值的字符串 |

#### 示例

``` JSON
{
    "type": "Decimal",
    "value": 1.23,
    "string": "1.23"
}
```

### LocationValue

经纬度位置值：

| 名称      | 类型   | 描述                                              |
| --------- | ------ | ------------------------------------------------- |
| type      | string | Location                                          |
| longitude | double | 经度值                                            |
| lantitude | double | 维度值                                            |
| string    | string | 用[]包起来的经度值和纬度值的字符串，中间以,分割， |

#### 示例

``` JSON
{
    "type": "Location",
    "longitude": 121.390234,
    "lantitude": 37.533733,
    "string": "[121.390234,37.533733]"
}
```

### BoolValue

布尔值：

| 名称 | 类型   | 描述     |
| ---- | ------ | -------- |
| type | string | Bool |
| value | boolean | 布尔值 |
| string | string | 布尔值的字符串 |

#### 示例


``` JSON
{
    "type": "Bool",
    "value": false,
    "string": "false"
}
```

### StringValue

字符串：

| 名称   | 类型   | 描述   |
| ------ | ------ | ------ |
| type   | string | String |
| value  | string | 字符串 |
| string | string | 字符串 |

#### 示例

``` JSON
{
    "type": "String",
    "value": "hello world",
    "string": "hello world"
}
```

### EnumValue

枚举值：

| 名称   | 类型   | 描述   |
| ------ | ------ | ------ |
| type   | string | Enum   |
| value  | string | 枚举值 |
| string | string | 枚举值 |

#### 示例

``` JSON
{
    "type": "Enum",
    "value": "蓝色",
    "string": "蓝色"
}
```

### DateValue

日期时间值：

| 名称   | 类型   | 描述                       |
| ------ | ------ | -------------------------- |
| type   | string | DateTime                   |
| value  | date   | 日期值                     |
| string | string | 按照日期格式格式化的日期值 |

#### 示例

``` JSON
{
    "type": "DateTime",
    "value": "2019-01-01T12:00:00.000+0000",
    "string": "2019-01-01 12:00:00"
}
```

### ArrayValue

数组值：

| 名称  | 类型            | 描述   |
| ----- | --------------- | ------ |
| type  | string          | Array  |
| value | [DataValue]()[] | 数组值 |

#### 示例

整数数组

``` JSON
{
    "type": "Array",
    "value": [
        {
            "type": "Int",
            "value": 1,
            "string": "1"
        },
        {
            "type": "Int",
            "value": 2,
            "string": "2"
        },
        {
            "type": "Int",
            "value": 3,
            "string": "3"
        },
        {
            "type": "Int",
            "value": 4,
            "string": "4"
        }
    ],
    "string": null
}
```

字符串数组

``` JSON
{
    "type": "Array",
    "value": [
        {
            "type": "String",
            "value": "Lorem ipsum dolor",
            "string": "Lorem ipsum dolor"
        },
        {
            "type": "String",
            "value": "sit amet consectetur adipisicing elit",
            "string": "sit amet consectetur adipisicing elit"
        },
        {
            "type": "String",
            "value": "Itaque voluptatem totam",
            "string": "Itaque voluptatem totam"
        },
        {
            "type": "String",
            "value": "architecto cupiditate officia rerum",
            "string": "architecto cupiditate officia rerum"
        },
        {
            "type": "String",
            "value": "error dignissimos praesentium libero ab nemo",
            "string": "error dignissimos praesentium libero ab nemo"
        }
    ],
    "string": null
}
```

### StructValue

结构值：

| 名称  | 类型                       | 描述   |
| ----- | -------------------------- | ------ |
| type  | string                     | Struct |
| value | map(string, [DataValue]()) | 结构值 |

#### 示例

``` JSON
{
    "type": "Struct",
    "value": {
        "probableCause": {
            "type": "String",
            "value": "error",
            "string": "error"
        },
        "perceivedSeverity": {
            "type": "Enum",
            "value": "红色",
            "string": "红色"
        }
    },
    "string": null
}
```

### ChoiceValue

任意数据值：

| 名称  | 类型                       | 描述         |
| ----- | -------------------------- | ------------ |
| type  | string                     | Choice       |
| value | map(string, [DataValue]()) | 某一个数据值 |

#### 示例

Choice数据类型中整数数据类型值。

``` JSON
{
    "type": "Choice",
    "value": {
        "c1": {
            "type": "Struct",
            "value": {
                "a": {
                    "type": "Int",
                    "value": 1,
                    "string": "1"
                }
            },
            "string": null
        }
    },
    "string": null
}
```

Choice数据类型中小数数据类型值。

``` JSON
{
    "type": "Choice",
    "value": {
        "c2": {
            "type": "Struct",
            "value": {
                "a": {
                    "type": "Decimal",
                    "value": 12.3,
                    "string": "12.3"
                }
            },
            "string": null
        }
    },
    "string": null
}
```

Choice数据类型中位置数据类型值。

``` JSON
{
    "type": "Choice",
    "value": {
        "c3": {
            "type": "Struct",
            "value": {
                "a": {
                    "type": "Location",
                    "longitude": 121.390234,
                    "latitude": 37.533733,
                    "string": "[121.390234, 37.533733]"
                }
            },
            "string": null
        }
    },
    "string": null
}
```

Choice数据类型中字符串数据类型值。

``` JSON
{
    "type": "Choice",
    "value": {
        "c4": {
            "type": "Struct",
            "value": {
                "a": {
                    "type": "String",
                    "value": "Lorem ipsum dolor, sit amet consectetur adipisicing elit.",
                    "string": "Lorem ipsum dolor, sit amet consectetur adipisicing elit."
                }
            },
            "string": null
        }
    },
    "string": null
}
```

