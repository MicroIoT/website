统一查询API为不同数据结构的数据提供基于json的统一，灵活的查询API，允许用户自定义查询条件，查询包括场地，设备，设备组，告警，事件等对象信息。统一查询API在应用端使用，设备端不能调用。统一查询有以下几种查询方式：

- 按id查询对象
- 按查询条件查询对象
- 按查询条件查询对象列表
- 按查询条件查询对象列表页
- 按查询条件查询对象数量
- 按查询条件查询对象是否存在
- 按查询条件查询distinct对象

统一查询API通过http连接获取平台查询结果，因此使用`HttpClientSession`类建立与MicroIoT平台的连接。统一查询需要用户根据自己的需求编写基于json的查询条件，如何编写查询条件在API参考[统一查询](../reference/query/query.md#_2)部分有详细介绍。

## 按id查询对象

物联网应用可以通过id查询相应对象信息，用户只需要指定查询的对象，以及对象的id。下面是根据设备id查询设备信息的代码。

```java
@SpringBootApplication(exclude={MongoAutoConfiguration.class})
public class QueryDemoApplication implements CommandLineRunner{
	@Autowired
	private HttpClientSession session;
	
	public static void main(String[] args) {
		SpringApplication.run(QueryDemoApplication.class, args);
	}

	@Override
	public void run(String... args) throws Exception {
        String deviceId = "5ddb83fb0e8e3d0001f60ed3";
		Device device = session.getEntityById(Device.class, deviceId);
		System.out.println(device.getString());
	}
}
```

这段代码使用`HttpClientSession`建立连接，Spring容器会在启动时自动注入连接会话，`getEntityById`方法根据id和对象类型信息返回对象的详细信息。

!!! note "注意"
    代码在@SpringBootApplication注解上加上了exclude={MongoAutoConfiguration.class}，禁止自动启动mongoDB配置，这是因为MicroIoT API for JAVA中加载的Spring Boot中mongoDB的配置会自动连接本地localhost:27017的mongoDB。

## 按查询条件查询对象

当应用端需要查询符合条件的某一个对象时，可以使用本API。下面是一个查询设备静态属性locked值为true，名称以0开头的设备信息示例程序。

```java
@SpringBootApplication(exclude={MongoAutoConfiguration.class})
public class QueryDemoApplication implements CommandLineRunner{
	@Autowired
	private HttpClientSession session;
	
	public static void main(String[] args) {
		SpringApplication.run(QueryDemoApplication.class, args);
	}

	@Override
	public void run(String... args) throws Exception {
        QueryInfo info = new QueryInfo();
		info.setFilter("{ name: /^0/, \“attribute.locked. value\”: true}");
        info.setSort("{ connected: -1 }");
        
		device = session.getOneEntity(Device.class, info);
		System.out.println(device.getString());
	}
}
```

用户需要在`QueryInfo`类的实例中指定`filter`查询条件和`sort`排序条件，`getOneEntity`方法会根据查询条件和排序条件查询符合条件的第一个对象信息。



## 按查询条件查询对象列表

按查询条件查询对象列表API与上一个API类似，只是返回的结果是列表。由于列表是参数化类型，所以需要使用`ParameterizedTypeReference`传递列表的参数化类型信息。

```java
@SpringBootApplication(exclude={MongoAutoConfiguration.class})
public class QueryDemoApplication implements CommandLineRunner{
	@Autowired
	private HttpClientSession session;
	
	public static void main(String[] args) {
		SpringApplication.run(QueryDemoApplication.class, args);
	}

	@Override
	public void run(String... args) throws Exception {
        QueryInfo info = new QueryInfo();
		info.setFilter("{ \"attributes.model.value\": \"a1\"}");
        info.setSort("{ name: -1 }");
        
		List<Device> devices = session.getEntityList(Device.class, info, new ParameterizedTypeReference<List<Device>>() {});
		for(Device device: devices) {
			System.out.println(device.getString());
		}
	}
}
```

`getEntityList`方法返回符合条件的对象列表，查询条件为静态属性model值为a1的设备列表，按name降序排序。

## 按查询条件查询对象列表页

查询列表页方法`getEntityPage`按页返回对象信息，用户除了输入查询条件和排序条件外，还可以指定查询哪一页，每页包含多少对象。列表页也是参数化类型，也需要使用`ParameterizedTypeReference`传递列表页的参数化类型信息。`RestPage`类是`Page`的具体实现类。下面的例子查询的是设备id为5ddb83fb0e8e3d0001f60ed3的属性location事件信息，按事件上报时间升序排序，显示第一页，每页有10条事件信息。

```java
@SpringBootApplication(exclude={MongoAutoConfiguration.class})
public class QueryDemoApplication implements CommandLineRunner{
	@Autowired
	private HttpClientSession session;
	
	public static void main(String[] args) {
		SpringApplication.run(QueryDemoApplication.class, args);
	}

	@Override
	public void run(String... args) throws Exception {
        QueryPageInfo page = new QueryPageInfo();
		page.setFilter("{ \"notifyObject.$id\": ObjectId(\"5ddb83fb0e8e3d0001f60ed3\"), \"attribute\": \"location\" }");
		page.setSort("{ reportTime: 1 }");
		page.setPageNumber(0);
		page.setPageSize(10);
		
		Page<Event> eventPage = session.getEntityPage(Event.class, page, new ParameterizedTypeReference<RestPage<Event>>() {});
		for(Event event : eventPage.getContent()) {
			System.out.println(event.getNotifyObject().getString());
			Location location = (Location) event.getData(Location.class);
			System.out.println(location.getLongitude() + "," + location.getLatitude());
		}
	}
}
```

## 按查询条件查询对象数量

查询对象数量方法`count`，输入查询条件返回符合条件的对象数量。下面的代码查询所有场地的数量。

```java
@SpringBootApplication(exclude={MongoAutoConfiguration.class})
public class QueryDemoApplication implements CommandLineRunner{
	@Autowired
	private HttpClientSession session;
	
	public static void main(String[] args) {
		SpringApplication.run(QueryDemoApplication.class, args);
	}

	@Override
	public void run(String... args) throws Exception {
        int count = session.count(Site.class, null);
		System.out.println("query count: " + count);
	}
}
```



## 按查询条件查询对象是否存在

查询对象数量方法`exist`，输入查询条件返回符合条件的对象是否存在。下面的代码查询名称以0开头的设备是否存在。

```java
@SpringBootApplication(exclude={MongoAutoConfiguration.class})
public class QueryDemoApplication implements CommandLineRunner{
	@Autowired
	private HttpClientSession session;
	
	public static void main(String[] args) {
		SpringApplication.run(QueryDemoApplication.class, args);
	}

	@Override
	public void run(String... args) throws Exception {
        QueryInfo info = new QueryInfo();
        info.setFilter("{ name: /^0/ }");
        
        boolean exist = session.exist(Device.class, info);
		System.out.println("query exist: " + exist);
	}
}
```



## 按查询条件查询distinct对象

查询distinct对象方法`getEntityDistinct`可以对对象的某个字段查询符合查询条件的distinct值，distinct值可以是一个完整的对象，或者只是一个简单的值。`getEntityDistinct`返回的是列表，也需要`ParameterizedTypeReference`传递列表的参数化类型信息。下面的例子查询条件是名称以0开头的场地，查询这些场地的siteType字段，返回distinct场地类型对象信息，因此`ParameterizedTypeReference`传递的是`List<SiteType>`。如果返回的是简单值，比如是String，则`ParameterizedTypeReference`传递`List<String>`。

```java
@SpringBootApplication(exclude={MongoAutoConfiguration.class})
public class QueryDemoApplication implements CommandLineRunner{
	@Autowired
	private HttpClientSession session;
	
	public static void main(String[] args) {
		SpringApplication.run(QueryDemoApplication.class, args);
	}

	@Override
	public void run(String... args) throws Exception {
        DistinctInfo distinct = new DistinctInfo();
        distinct.setField("siteType");
		distinct.setReturnClass(SiteType.class);
        distinct.setFilter("{ name: /^0/ }");
        
		List<SiteType> types = session.getEntityDistinct(Site.class, distinct, new ParameterizedTypeReference<List<SiteType>>() {});
		for(SiteType type : types) {
			System.out.println(type.getName());
		}
	}
}
```

