# MicroIoT REST API

MicroIoT Representational State Transfer (REST) API 是基于Bearer Token的用户认证方式访问MicroIoT平台的资源。Bearer Token通过Authorization Header发送给MicroIoT平台实现用户认证。

``` HTTP
GET /resource HTTP/1.1
Host: www.microiot.top/server
Authorization: Bearer eyJhbGciOiJIUzUxMiJ9.eyJzdWIiOiJhZG1pbiIsInNjb3BlcyI6ImFkbWluIiwiaXNzIjoibWljcm9pb3QiLCJpYXQiOjE1NzQ5OTI1MDAsImV4cCI6MTU3NDk5NjEwMH0.AwW6e6gy90SddDwbIIYBU1aCJhhHbduXR-lFQLS4nkWtR7JzSeBI0-3sMxqYqHmR0oUueWW8IhiKzmbERUQSOg
```

使用MicroIoT REST API的步骤如下：

1. 注册MicroIoT平台用户，获取MicroIoT平台用户账号。注册网址为[https://www.microiot.top/studio/#/register](https://www.microiot.top/studio/#/register)
2. 调用用户认证API，获取token和refresh token。详细内容见[用户登录](./auth/login.md)
3. 在调用MicroIoT REST API时，在 Authorization header 中携带token，其他请求信息可以在请求参数中，也可以在请求体中，请求体内容采用json格式，所以需要在请求Headers中设置`Content-type`为 `application/json`。如果调用成功，返回的http status code为200，响应体内容为json格式。
4. MicroIoT平台token过期时间默认为一小时，如果token过期，可以使用refresh toke调用刷新token API，重新获取token和refresh token。详细内容见[刷新token](./auth/refresh.md)。

