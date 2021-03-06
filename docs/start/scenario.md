# 应用场景

MicroIoT可以广泛应用于各种物联网场景，比如在智能家居领域，空调，洗衣机，冰箱，电饭锅，微波炉，电视，照明灯，监控，智能门锁等各种家电都可以通过MicroIoT平台远程控制。在智慧物流领域，物流的运输、仓储、包装、装卸、配送等各个环节都可以使用MicroIoT实现系统感知。本节将详细描述两个应用场景在MicroIoT平台中的具体实现，希望能激发MicroIoT用户更有创意的想法。

## 广告播控系统

广告播控系统是提供功能强大的广告素材准备，版面编辑、传输、发布和管理的专业平台。可以实时控制广告播放的版面，内容，字幕等。广告播控系统使用MicroIoT平台实现对广告终端的监控。广告播控系统架构如下：

![img40](../img/img40.png)

广告播控系统通过MicroIoT 应用端API监控广告终端，在设备端则使用MicroIoT提供的设备端API接收系统命令，处理后通过API返回响应信息。广告终端可以同时播放多个广告版面，每个版面播放不同的多媒体素材，可以控制终端字幕显示，控制html模板素材显示的内容。在播放广告过程中出现问题，可以及时通知系统处理错误。广告终端设备类型定义如下：

![table4](../img/table4.png)

## 智能电表

智能电表是智能电网的智能终端，它不是传统意义上的电能表，智能电表除了具备传统电能表基本用电量的计量功能以外，为了适应智能电网和新能源的使用它还具有双向多种费率计量功能、用户端控制功能、多种数据传输模式的双向数据通信功能、防窃电功能等智能化功能。智能电表系统使用MicroIoT提供物联网服务，使用支付服务提供网上购电功能。

![img41](../img/img41.png)

智能电表是取代传统电表的新一代电表，智能电表具备双向通信能力，使用户更方便的了解自己用电情况，用户可以在网上购电，并自动写入电表中，当表内余额低于设定值时，可以发送短信通知用户。智能电表的设备类型定义如下表：

![table5](../img/table5.png)
