# 统一查询

MicroIoT平台可以灵活定义设备、场地，支持多达十种的动态数据类型，可以接收各种事件数据、告警数据。为了查询灵活定义的物联网大数据，MicroIoT平台提供了统一查询API。统一查询API不同于普通的查询API，普通查询API针对某个查询对象，查询条件是事先定义好的，统一查询为不同数据结构的数据提供基于json的统一，灵活的查询语言API 。用户可以按照需要自由定义查询条件，查询的对象包括场地，设备，设备组，告警，事件。

统一查询支持以下几种查询方式：

1. [按id查询对象](queryid.md)
2. [按查询条件查询对象](queryobject.md)
3. [按查询条件查询列表](querylist.md)
4. [按查询条件查询列表页](querypage.md)
5. [按地理位置查询条件查询列表](querygeo.md)
7. [按查询条件查询distinct列表](querydistinct.md)
8. [按查询条件查询数量](querycount.md)
9. [按查询条件查询是否存在](queryexist.md)

## 查询条件

下面列出查询对象时，不同的查询方式的查询条件的格式。查询条件的详细介绍参见[mongoDB查询文档]( https://docs.mongodb.com/manual/tutorial/query-documents/ )。

### 查询所有对象

查询所有对象，只需要输入空的json字符串。

``` JSON
{}
```

### 查询等于某个条件的对象

查询等于某个条件的对象，使用如下格式的json字符串。

``` JSON
{ <field>:<value>, ... }
```

下面这个例子是查询上线的设备的查询条件。

``` JSON
{ connected: true }
```

### 使用查询操作符查询对象

使用查询操作符查询对象的json字符串如下所示。

``` JSON
{ <field1>: { <operator1>: <value1> }, ... }
```

下面的例子是查询系统管理员和区域管理员用户的查询条件。

``` JSON
{ roles: { $in: [ "SYSTEM", "AREA" ] } }
```

关于查询操作符的详细描述参见[mongoDB查询操作符文档](https://docs.mongodb.com/manual/reference/operator/query/#query-selectors)。

### 使用 与 查询

使用 与 查询可以将多个查询条件组合在一起查询对象。

下面的例子是查询值大于5并且上报时间在2019年10月1日之后的对象。

``` JSON
{ value: { $lt: 5 }, reportTime: { $gte: new ISODate("2019-10-01") } }
```

### 使用 或 查询

使用 或 查询可以组合多个查询条件，查询符合至少一个查询条件的对象。

下面的例子是查询值大于5或者上报时间在2019年10月1日之后的对象。

``` JSON
{ $or: [ { value: { $lt: 5 }, reportTime: { $gte: new ISODate("2019-10-01") } } ] }
```

## 排序

排序指定查询返回结果的顺序，排序的json格式如下格式：


``` JSON
{ <field>:<value>, ... }
```
排序可以分为升序排序和降序排序，升序则value为1，降序则value为-1。

下面的例子对查询返回的结果对age字段降序排序，对status字段升序排序。

``` JSON
{ age: -1, status: 1, }
```

对排序的详细介绍参见[mongoDB排序文档](https://docs.mongodb.com/manual/reference/method/cursor.sort/)。

