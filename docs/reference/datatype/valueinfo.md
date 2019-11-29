## AttValueInfo

属性值输入是用于输入属性值的数据类型。

| 名称        | 类型                          | 必选 | 描述                                                         |
| ----------- | ----------------------------- | ---- | ------------------------------------------------------------ |
| value       | string                        | 否   | 简单数据类型属性值，Location数据类型输入的经纬度中间用逗号分开，前一个值是经度，后一个值是维度。其他简单数据类型属性值都可以用字符串输入。 |
| arrayValue  | [AttValueInfo]()[]            | 否   | Array数据类型属性值                                          |
| structValue | map(string, [AttValueInfo]()) | 否   | Struct或Choice数据类型属性值                                 |

## 示例

### Location数据类型属性值输入

``` JSON
{
    "value": "121.390234,37.533733"
}
```

### Struct Array数据类型属性值输入

下面的结构数组数据类型的类型定义参见[属性类型定义示例](typeinfo.md#struct-array)。

``` JSON
{
    "arrayValue": [
        {
            "structValue": {
                "probableCause": {
                    "value": "unknow reason"
                },
                "perceivedSeverity": {
                    "value": "红色"
                }
            }
        },
        {
            "structValue": {
                "probableCause": {
                    "value": "failure"
                },
                "perceivedSeverity": {
                    "value": "蓝色"
                }
            }
        },
        {
            "structValue": {
                "probableCause": {
                    "value": "error"
                },
                "perceivedSeverity": {
                    "value": "绿色"
                }
            }
        }
    ]
}
```

