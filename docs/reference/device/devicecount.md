# 设备数量

查询设备数量。查询结果只返回当前领域内符合查询条件的设备数量。

``` HTTP
GET https://www.microiot.top/server/devices/count?locationId={locationId}&siteTypeId={siteTypeId}&name={name}
```
## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称         | 类型   | 必选 | 描述               |
| ------------ | ------ | ---- | ------------------ |
| locationId   | string | 否   | 父场地id           |
| deviceTypeId | string | 否   | 设备类型id         |
| name         | string | 否   | 对设备名称正则查询 |

## 请求体

无

## 响应

| 状态 | 类型 | 描述     |
| ---- | ---- | -------- |
| 200  | int  | 设备数量 |



## 示例

### 请求URI示例

查询设备类型id为5dd67dba0e8e3d00012613ff的设备数量：

``` HTTP
GET https://www.microiot.top/server/devices/count?deviceTypeId=5dd67dba0e8e3d00012613ff
```
