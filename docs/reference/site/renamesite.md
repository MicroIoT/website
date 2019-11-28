# 重命名场地

修改一个场地的名称。

``` HTTP
PATCH https://www.microiot.top/server/sites/name
```
系统管理员和区域管理员都可以重命名场地，但是区域管理员只能重命名自己负责的区域内的场地。修改场地名称后，平台会发出AttributeChangedAlarm告警通知应用端。

## 访问控制

| 访问用户角色           | 是否需要认证                                 |
| :--------------------- | :------------------------------------------- |
| 系统管理员或区域管理员 | 是，使用Bearer Token认证，具体信息见登录授权 |


## 请求体

| 名称 | 类型   | 必选 | 描述       |
| ---- | ------ | ---- | ---------- |
| id   | string | 是   | 场地id     |
| name | string | 是   | 场地新名称 |


## 响应

| 状态 | 类型                    | 描述               |
| ---- | ----------------------- | ------------------ |
| 200  | [Site](addsite.md#site) | 成功修改名称的场地 |



## 示例

### 请求体示例

``` JSON
{
    "id": "5ddb2fbe0e8e3d0001f60ec9",
    "name": "test"
}
```

### 响应示例

参见[场地信息](addsite.md#_7)。
