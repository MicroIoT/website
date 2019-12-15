# 上报事件

上报一个新的事件。

!!! info "http"
    POST https://www.microiot.top/server/events

## 访问控制

| 访问用户角色 | 是否需要认证                                 |
| :----------- | :------------------------------------------- |
| 设备         | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |


## 请求体

| 名称       | 类型                                                         | 必选 | 描述                                        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------- |
| values     | map(string, [AttValueInfo](../datatype/valueinfo.md#attvalueinfo)) | 是   | 事件信息，key为属性名称，value为属性值      |
| reportTime | string                                                       | 是   | 事件上报时间，日期格式为yyyy-MM-dd HH:mm:ss |

## 响应

| 状态 | 类型 | 描述 |
| ---- | ---- | ---- |
| 200  |      |      |



## 示例

### 请求体示例

``` JSON
{
    "reportTime": "2000-01-06 21:01:08",
    "values": {
        "thresholdInfo": {
            "value": "423"
        },
        "notificationIdentifier": {
            "value": "23.2"
        },
        "trendIndication": {
            "value": "true"
        }
    }
}
```

