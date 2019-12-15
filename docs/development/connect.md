## 连接会话

MicroIoT API for JAVA使用连接会话类建立与MicroIoT平台的连接。连接会话类一共有四种：

- `HttpClientSession`：应用端http连接会话类
- `WebsocketClientSession`：应用端websocket连接会话类
- `HttpDeviceSession`：设备端http连接会话类
- `WebsocketDeviceSession`：设备端websocket连接会话类

http连接会话支持应用端或设备端建立与MicroIoT平台之间的http连接。应用端使用http连接会话查询数据，管理MicroIoT平台，设备端使用http连接会话上报告警和事件信息，以及与该设备相关的信息查询。

websocket连接会话支持应用或设备端建立与MicroIoT平台之间的websocket连接，websocket连接会话建立在http连接会话基础上，通过websocket连接会话可以得到相应的http连接会话。应用端使用websocket连接会话读取、设置、操作物联网设备，还可以通过websocket连接会话订阅告警。设备端使用websocket连接会话响应读取、设置、操作请求，也可以通过websocket连接会话读取、设置、操作设备组内的设备，订阅设备组内设备的告警。

MicroIoT API for JAVA使用注解建立http连接会话和websocket连接会话，在系统启动时，会话类根据Spring Boot配置文件中的连接配置参数自动建立与平台的连接。

## 连接配置

连接会话使用Spring Boot的配置文件配置连接信息，建立与MicroIoT平台的连接，其中最重要的的一个参数是MicroIoT URI，用于指定MicroIoT平台地址，另外还可以在建立连接时配置一些其他连接参数。应用端连接与设备端连接稍有一些不同，建立应用端连接时还需要指定物联网应用工作的领域。

### MicroIoT URI

MicroIoT API for JAVA使用MicroIoT URI建立与MicroIoT平台的连接。MicroIoT URI的格式如下：

```MicroIoT
[protocol]://[host][:port]
```

其中protocol指定了连接的协议，可以是iotp协议，也可以是iotps，iotp是Internet of Things Protocol的缩写，s代表security。

下面是一个MicroIoT URI例子：

```
iotps：//www.microiot.top/server
```

### 连接配置参数

MicroIoT API for JAVA使用http协议和websocket协议建立与MicroIoT平台的连接，用户可以通过配置以下参数配置http连接和websocket连接。

| 参数                                                | 默认值       | 描述                                  |
| --------------------------------------------------- | ------------ | ------------------------------------- |
| microiot.httpclient.connectTimeout                  | 20000        | 建立http连接的超时时间                |
| microiot.httpclient.requestTimeout                  | 20000        | http连接不够用的等待时间              |
| microiot.httpclient.socketTimeout                   | 30000        | 每次http请求等待返回的超时时间        |
| microiot.httpclient.defaultMaxPerRoute              | 100          | 每个主机最大http连接数                |
| microiot.httpclient.maxTotalConnections             | 300          | 最大http连接数                        |
| microiot.httpclient.defaultKeepAliveTimeMillis      | 20000        | 默认http连接保持活跃的时间            |
| microiot.httpclient.closeIdleConnectionWaitTimeSecs | 30           | 空闲http连接生存的时间                |
| microiot.websocket.timeout                          | 100          | websocket请求响应的超时时间，单位为秒 |
| microiot.websocket.heartbeat                        | 10000, 10000 | 进入和出去的心跳间隔时间，单位为毫秒  |
| microiot.websocket.message-buffer-size              | 20971520     | 文本消息的最大缓存                    |

## 示例

下面是一个应用端Spring Boot配置文件application.properties文件配置连接的例子，其中配置了每次http请求等待返回的超时时间和websocket请求响应的超时时间：

```application.properties
microiot.connect.username=admin
microiot.connect.password=password
microiot.connect.uri=iotps://www.microiot.top/server
microiot.connect.domain=admin

microiot.httpclient.socketTimeout=10000
microiot.websocket.timeout=10
```

上面是一个应用端配置的示例，如果是配置设备端，则不需要配置`microiot.connect.domain`参数。
