上一节讲解了应用端设备监控API的使用，应用端设备监控只是发起监控请求，整个监控流程必须有设备端配合响应请求才能形成完整过程，本节将讲解如何使用设备端监控API响应请求，上报告警、事件信息。设备端和应用端一样使用websocket连接，因此使用`WebsocketDeviceSession`类建立与MicroIoT平台的连接。调试设备端程序时，可以使用MicroIoT Studio发起读取、设置、操作设备的请求，接收上报的告警信息，查询上报的事件信息。

MicroIoT API提供了`IoTDevice`类用于初始化设备，指定该设备读取、设置、操作对应的处理逻辑。下面是一个设备的例子，它的读取、设置、操作对应的处理类分别是`GetHandler`，`SetHandler`，`ActionHandler`。

```java
@SpringBootApplication(exclude={MongoAutoConfiguration.class})
public class DeviceDemoApplication implements CommandLineRunner{
	@Autowired
	private WebsocketDeviceSession session;
	@Autowired
	private GetHandler onGet;
	@Autowired
	private SetHandler onSet;
	@Autowired
	private ActionHandler onAction;
	
	public static void main(String[] args) {
		SpringApplication.run(DeviceDemoApplication.class, args);
	}
	@Override
	public void run(String... args) throws Exception {
		new IoTDevice(session, onGet, onSet, onAction);
	}
}
```

## 响应读取设备属性值

实现设备端读取处理类，需要继承MicroIoT API提供的`GetRequestSubscriber`类，实现`getAttributeValue`方法，其中参数requester是请求者信息，device是设备的信息，attribute是属性名称。下面是智能车锁的响应读取属性值的实现代码。


```java
@Component
@Scope("prototype")
public class GetHandler extends GetRequestSubscriber {

	@Override
	public Object getAttributeValue(User requester, Device device, String attribute) {
		if(attribute.equals("location")) {
			Location location = getLocation();
			return location;
		}else if(attribute.equals("locked")) {
			boolean locked = getLocked();
			return locked;
		}else {
			throw new ValueException("get unknow attribute: " + attribute);
		}
	}
}
```

## 响应设置设备属性值

实现设备端设置处理类，需要继承MicroIoT API提供的`SetRequestSubscriber`类，实现`init`方法和`setAttribute`方法，`init`方法用于设置属性值的数据类型，`setAttribute`方法实现设置设备属性值的处理逻辑。下面的代码是智能车锁在收到设置locked属性请求后，上报StateChangedAlarm告警。


```java
@Component
@Scope("prototype")
public class SetHandler extends SetRequestSubscriber {
	
	@Override
	public void init() {
		addType("locked", boolean.class);
	}

	@Override
	public void setAttribute(User requester, Device device, String attribute, Object value) {
		if(attribute.equals("locked")) {
			boolean locked = (boolean)value;
			Location location = getLocation();
			StateChangedAlarm alarm = new StateChangedAlarm(location, locked);
			this.getWebsocketDeviceSession().getSession().reportAlarm("StateChangedAlarm", alarm);
		} else {
			throw new ValueException("set unknonw attribute: " + attribute);
		}
	}
}
```



## 响应操作设备

实现设备端操作处理类，需要继承MicroIoT API提供的`ActionRequestSubscriber`类，实现`init`方法和`action`方法，`init`方法用于设置操作请求信息的数据类型，`action`方法用于实现具体的操作处理逻辑，并返回操作响应，参数`action`是操作名称，`request`是该操作的请求信息。下面是智能车锁的操作处理代码，其中`Filter`类和`Record`类已经在上一节中介绍过。

```java
@Component
@Scope("prototype")
public class ActionHandler extends ActionRequestSubscriber {
	
	@Override
	public void init() {
		addType("getHistory", Filter.class);
	}

	@Override
	public Object action(User requester, Device device, String action, Object request) {
		if(action.equals("getHistory")) {
			Filter filter = (Filter)request;
            
			List<Record> records = new ArrayList<Record>();
			for(int i = 0; i < 10; i ++) {
				Record record = getRecord(filter);
				records.add(record);
			}

			return records;
		}else {
			throw new ValueException("unknonw action: " + action);
		}
	}
}
```

## 上报告警、事件信息

设备端上报告警、事件信息是通过http连接上报，在前面的响应设置属性值的部分已经介绍过通过`HttpDeviceSession`类上报告警，下面介绍另外一种上报告警和事件的方式，就是使用`IoTDevice`类的方法`reportAlarm`和`reportEvent`，其实`IoTDevice`类的这两个方法最后还是调用`HttpDeviceSession`类实现上报告警、事件。上报告警时只需要指定告警类型，及其告警信息，上报事件时可以同时上报多个属性值。下面是智能车锁在系统启动后上报StateChangedAlarm告警和location属性事件的例子，其中`StateChangedAlarm`类已经在上一节中介绍过。


```java
@SpringBootApplication(exclude={MongoAutoConfiguration.class})
public class ReportDemoApplication implements CommandLineRunner{
	@Autowired
	private WebsocketDeviceSession session;
	
	public static void main(String[] args) {
		SpringApplication.run(ReportDemoApplication.class, args);
	}
	@Override
	public void run(String... args) throws Exception {
		IoTDevice device = new IoTDevice(session, null, null, null);
		
		StateChangedAlarm alarm = getAlarm();
		device.reportAlarm("StateChangedAlarm", alarm);
		
		Map<String, Object> events = new HashMap<String, Object>();
		Location location = getLocation();
		events.put("location", location);
		device.reportEvent(events);
	}
}
```

## 设备组

普通的设备只能被动的被应用端监控，但是当若干设备组成了一个设备组，这些设备就不只是能被动的接收请求，也可以作为应用端监控设备组内的其他设备，订阅这些设备的告警信息。设备组就是为了设备之间相互协作配合而建立的。MicroIoT API为支持设备组编程，提供了`getMyDeviceGroup`方法，设备端可以查询自己的设备组信息。另外应用端的读取、设置、操作方法`get`，`set`，`action`都可以在设备组内的设备端使用，与应用端使用方式完全一样，只需要从`IoTDevice`类中通过`getDeviceSession`方法得到`WebsocketDeviceSession`即可。

