# 按地理位置查询条件查询对象列表页

查询距离中心位置最大距离范围内符合查询条件的对象。返回结果必须在当前领域范围内。

!!! info "http"
    GET https://www.microiot.top/server/{queryObject}/query/geo?x={x}&y={y}&maxDistance={maxDistance}&metrics={metrics}&filter={filter}&sort={sort}

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求参数

| 名称        | 类型                                      | 必选 | 描述                     |
| ----------- | ----------------------------------------- | ---- | ------------------------ |
| queryObject | [QueryObject](queryid.md#queryobject)     | 是   | 查询对象                 |
| x           | double                                    | 是   | 查询中心位置x坐标        |
| y           | double                                    | 是   | 查询中心位置y坐标        |
| maxDistance | double                                    | 是   | 查询距离中心位置最大距离 |
| metrics     | [Metric](../datatype/georesult.md#metric) | 否   | 距离单位                 |
| filter      | string                                    | 否   | 查询过滤条件             |
| sort        | string                                    | 否   | 查询排序                 |
| pageNumber  | int                                       | 否   | 当前页数，缺省为0        |
| pageSize    | int                                       | 否   | 每页显示数，缺省为10     |

## 请求体

无

## 响应

| 状态 | 类型                                              | 描述         |
| ---- | ------------------------------------------------- | ------------ |
| 200  | [GeoResults](../datatype/georesult.md#georesults) | 地理位置结果 |



## 示例

### 请求URI示例

!!! info "http"
    GET https://www.microiot.top/server/sites/query/geo?x=101&y=37&maxDistance=1000&sort={ name: -1 }&pageSize=5


