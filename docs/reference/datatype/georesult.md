## GeoResults

GeoResults用于返回距离中心点最大距离范围内的地理位置信息，数据类型定义如下：  

| 名称            | 类型                      | 描述                 |
| --------------- | ------------------------- | -------------------- |
| averageDistance | [Distance](#distance)     | 平均距离信息         |
| content         | [GeoResult](#georesult)[] | 地理位置结果信息数组 |

## GeoResult

| 名称     | 类型                                                         | 描述         |
| -------- | ------------------------------------------------------------ | ------------ |
| content  | [Device](../device/adddevice.md#device)或[Site](../site/addsite.md#site)或[Event](../event/addevent.md#event)或[Alarm](../alarm/addalarm.md#alarm) | 结果对象     |
| distance | [Distance](#distance)                                        | 到中心点距离 |

## Distance

距离信息。

| 名称   | 类型              | 描述     |
| ------ | ----------------- | -------- |
| value  | double            | 距离值   |
| metric | [Metric](#metric) | 距离单位 |

## Metric

距离单位，缺省单位为米。

| 名称 | 类型   | 描述 |
| ---- | ------ | ---- |
| KILOMETERS   | string | 公里 |
| MILES   | string | 英里 |
| NEUTRAL   | string | 米 |



## 示例

``` JSON
{
    "averageDistance": {
        "value": 20.897055071706617,
        "metric": "NEUTRAL"
    },
    "content": [
        {
            "content": {
                "id": "5cae8fdded22362794f3feb0",
                "name": "002",
                "parent": null,
                "siteType": {
                    "id": "5cae8a52ed22362794f3feae",
                    "name": "智慧公厕",
                    "description": "智慧公厕，可以实时监控公厕环境信息，占位信息",
                    "attDefinition": {
                        "city": {
                            "dataType": {
                                "type": "String",
                                "min": 0,
                                "max": 255
                            },
                            "optional": true,
                            "description": "公厕所在城市"
                        },
                        "district": {
                            "dataType": {
                                "type": "String",
                                "min": 0,
                                "max": 255
                            },
                            "optional": true,
                            "description": "公厕所在区"
                        },
                        "description": {
                            "dataType": {
                                "type": "String",
                                "min": 0,
                                "max": 255
                            },
                            "optional": true,
                            "description": "公厕的描述"
                        },
                        "location": {
                            "dataType": {
                                "type": "Location"
                            },
                            "optional": false,
                            "description": "公厕的经纬度位置"
                        },
                        "url": {
                            "dataType": {
                                "type": "Array",
                                "dataType": {
                                    "type": "String",
                                    "min": 0,
                                    "max": 1024
                                }
                            },
                            "optional": true,
                            "description": "公厕的图片url"
                        }
                    }
                },
                "attributes": {
                    "city": {
                        "type": "String",
                        "value": "北京市",
                        "string": "北京市"
                    },
                    "district": {
                        "type": "String",
                        "value": "海淀区",
                        "string": "海淀区"
                    },
                    "location": {
                        "type": "Location",
                        "longitude": 121.390234,
                        "lantitude": 37.533733,
                        "string": "[121.390234, 37.533733]"
                    },
                    "url": {
                        "type": "Array",
                        "value": [
                            {
                                "type": "String",
                                "value": "https://smartwc.oss-cn-beijing.aliyuncs.com/5af0408b01d8d.jpg",
                                "string": "https://smartwc.oss-cn-beijing.aliyuncs.com/5af0408b01d8d.jpg"
                            },
                            {
                                "type": "String",
                                "value": "https://smartwc.oss-cn-beijing.aliyuncs.com/5af0409ed49a5.jpg",
                                "string": "https://smartwc.oss-cn-beijing.aliyuncs.com/5af0409ed49a5.jpg"
                            },
                            {
                                "type": "String",
                                "value": "https://smartwc.oss-cn-beijing.aliyuncs.com/5afe328357e4a.jpg",
                                "string": "https://smartwc.oss-cn-beijing.aliyuncs.com/5afe328357e4a.jpg"
                            }
                        ],
                        "string": null
                    }
                },
                "string": "002智慧公厕"
            },
            "distance": {
                "value": 20.39721827823699,
                "metric": "NEUTRAL"
            }
        },
        {
            "content": {
                "id": "5cae8f90ed22362794f3feaf",
                "name": "001",
                "parent": null,
                "siteType": {
                    "id": "5cae8a52ed22362794f3feae",
                    "name": "智慧公厕",
                    "description": "智慧公厕，可以实时监控公厕环境信息，占位信息",
                    "attDefinition": {
                        "city": {
                            "dataType": {
                                "type": "String",
                                "min": 0,
                                "max": 255
                            },
                            "optional": true,
                            "description": "公厕所在城市"
                        },
                        "district": {
                            "dataType": {
                                "type": "String",
                                "min": 0,
                                "max": 255
                            },
                            "optional": true,
                            "description": "公厕所在区"
                        },
                        "description": {
                            "dataType": {
                                "type": "String",
                                "min": 0,
                                "max": 255
                            },
                            "optional": true,
                            "description": "公厕的描述"
                        },
                        "location": {
                            "dataType": {
                                "type": "Location"
                            },
                            "optional": false,
                            "description": "公厕的经纬度位置"
                        },
                        "url": {
                            "dataType": {
                                "type": "Array",
                                "dataType": {
                                    "type": "String",
                                    "min": 0,
                                    "max": 1024
                                }
                            },
                            "optional": true,
                            "description": "公厕的图片url"
                        }
                    }
                },
                "attributes": {
                    "city": {
                        "type": "String",
                        "value": "什邡市",
                        "string": "什邡市"
                    },
                    "location": {
                        "type": "Location",
                        "longitude": 122.390234,
                        "lantitude": 37.533733,
                        "string": "[122.390234, 37.533733]"
                    },
                    "url": {
                        "type": "Array",
                        "value": [
                            {
                                "type": "String",
                                "value": "https://smartwc.oss-cn-beijing.aliyuncs.com/5af0408b01d8d.jpg",
                                "string": "https://smartwc.oss-cn-beijing.aliyuncs.com/5af0408b01d8d.jpg"
                            },
                            {
                                "type": "String",
                                "value": "https://smartwc.oss-cn-beijing.aliyuncs.com/5af0409ed49a5.jpg",
                                "string": "https://smartwc.oss-cn-beijing.aliyuncs.com/5af0409ed49a5.jpg"
                            },
                            {
                                "type": "String",
                                "value": "https://smartwc.oss-cn-beijing.aliyuncs.com/5afe328357e4a.jpg",
                                "string": "https://smartwc.oss-cn-beijing.aliyuncs.com/5afe328357e4a.jpg"
                            }
                        ],
                        "string": null
                    }
                },
                "string": "001智慧公厕"
            },
            "distance": {
                "value": 21.396891865176244,
                "metric": "NEUTRAL"
            }
        }
    ]
}
```

