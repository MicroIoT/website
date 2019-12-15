# 刷新token

当认证token过期后，使用refresh token重新获取token凭证。

!!! info "http"
    GET https://www.microiot.top/server/token


## 访问控制

| 访问用户角色 | 是否需要认证                                                 |
| :----------- | :----------------------------------------------------------- |
| 任何人       | 是，使用Bearer Token认证，具体信息见[REST API认证](../api.md) |

## 请求体

无

## 响应

| 状态 | 类型                            | 描述      |
| ---- | ------------------------------- | --------- |
| 200  | [Token](../auth/login.md#token) | 认证token |

## 示例

### 响应示例

参见[token示例](../auth/login.md#_6)。
