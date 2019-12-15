数据类型在MicroIoT平台中是一个非常重要的概念，在定义设备类型的属性，操作，告警中都需要使用。在MicroIoT API for JAVA中支持对平台中的数据类型序列化/反序列化操作，方便物联网应用开发使用。MicroIoT平台支持的数据类型包括：

- 整数类型
- 小数类型
- 字符串类型
- 布尔类型
- 枚举类型
- 日期时间类型
- 经纬度位置类型
- 数组类型
- 结构类型
- 任意类型

## 整数类型

MicroIoT平台中的整数类型在java语言中用`int`代表，下面是对整数类型的属性读取和设置的示例程序。

```java
//读取整数类型属性
int value = session.get(deviceId, attribute, int.class);
//设置整数类型属性
session.set(deviceId, attribute, value);
```



## 小数类型

MicroIoT平台中的小数类型对应java中的`double`，下面是对小数类型的属性读取和设置的示例程序。

```java
//读取小数类型属性
double value = session.get(deviceId, attribute, double.class);
//设置小数类型属性
session.set(deviceId, attribute, value);
```



## 字符串类型

MicroIoT平台中的字符串类型对应java中的`String`，下面是对字符串类型的属性读取和设置的示例程序。

```java
//读取字符串类型属性
String value = session.get(deviceId, attribute, String.class);
//设置字符串类型属性
session.set(deviceId, attribute, value);
```



## 布尔类型

MicroIoT平台中的布尔类型对应java中的`boolean`数据类型，下面是对布尔类型的属性读取和设置的示例程序。

```java
//读取布尔类型属性
boolean value = session.get(deviceId, attribute, boolean.class);
//设置布尔类型属性
session.set(deviceId, attribute, value);
```



## 枚举类型

MicroIoT平台中的枚举类型对应java中的`enum`数据类型，在使用枚举类型前，必须先定义枚举类型的可能值。下面的例子是一个颜色的枚举类型。

```java
public enum Color {
	Red, Yellow, Blue, Purple, Black;
}
```

`enum Color`的可能值必须与MicroIoT平台中定义的枚举类型的可能值完全一致。下面是对枚举类型Color的属性的读取和设置的示例程序。

```java
//读取枚举类型属性
Color value = session.get(deviceId, attribute, Color.class);
//设置枚举类型属性
session.set(deviceId, attribute, value);
```



## 日期时间类型

MicroIoT平台中的日期时间类型对应java中的`java.util.Date`数据类型，下面是对日期时间类型属性的读取和设置的示例程序。

```java
//读取日期时间类型属性
Date value = session.get(deviceId, attribute, Date.class);
//设置日期时间类型属性
session.set(deviceId, attribute, value);
```



## 经纬度位置类型

MicroIoT API for JAVA定义了`top.microiot.domain.attribute.Location`类代表MicroIoT平台中的经纬度位置类型，下面是对经纬度位置类型属性的读取和设置的示例程序。

```java
//读取经纬度位置类型属性
Location value = session.get(deviceId, attribute, Location.class);
//设置经纬度位置类型属性
Location location = new Location(longitude, latitude);
session.set(deviceId, attribute, location);
```

## 结构类型

MicroIoT平台中的结构类型对应java中的POJO对象，在定义结构类型的POJO对象时，POJO对象的属性名称必须与MicroIoT平台中定义的结构类型的属性名称完全一致，属性的数据类型也必须保持一致。前面设备监控一节中介绍的[Filter](client.md#filter)类，[Record](client.md#record)类，[StateChangedAlarm](client.md#statechangedalarm)类都是结构类型的例子。如果有一个设备的属性，它的数据类型是Filter结构，那么对这个属性的读取和设置的示例程序如下。

```java
//读取Filter类型属性
Filter value = session.get(deviceId, attribute, Filter.class);
//设置Filter类型属性
Filter filter = new Filter(startDate, endDate);
session.set(deviceId, attribute, filter);
```



## 数组类型

MicroIoT平台中的数组类型可以对应java的`java.util.List`，也可以对应`java.util.Set`，`List`和`Set`作为集合类，可以存储任何类型的数据，在定义数组类型时，需要先定义`List`或`Set`内存储的数据类型。前面介绍的[Record](client.md#record)数组，就是数组类型的例子。如果有一个设备的属性，它的数据类型是Record数组，那么对这个属性的读取和设置的示例程序如下。`List`和`Set`集合类，不同与前面介绍的数据类型，它除了要定义使用的集合类，还需要定义集合类的类型参数，所以需要使用`ParameterizedTypeReference`定义参数化类型信息。

```java
//读取Record数组类型属性
List<Record> value = session.get(deviceId, attribute, new ParameterizedTypeReference<List<Record>>() {});
//设置Record数组类型属性
List<Record> records = new ArrayList<Record>();
session.set(deviceId, attribute, records);
```



## 任意类型

MicroIoT平台中的任意类型是数据类型的集合，类似java中的继承关系，任意类型中的每一个数据类型在java中都继承自同一个父类。下面是MicroIoT Studio中定义的一个任意类型，它可以是一个整数类型，也可以是一个小数类型，或者是位置类型，或者字符串类型共四种选择。


![](..\img\img46.png)


![](..\img\img47.png)


![](..\img\img45.png)


![](..\img\img48.png)

在定义任意类型的java类时，首先需要定义它们的父类，下面是它们的父类`TestChoice`的定义。


```java
public abstract class TestChoice {

}
```

定义了父类后就可以开始定义每一个具体类，所有的具体类都必须继承自前面定义的父类，而类的名称必须与MicroIoT平台定义任意类型中的选项名称一致。在我们这个任意类型的例子中有四个选项：C1，C2，C3，C4。因此在定义具体类时，必须使用这些名称，而类内部的属性定义与结构类型的定义一样，POJO对象的属性名称必须与MicroIoT平台中定义的结构类型的属性名称完全一致，属性的数据类型也必须保持一致。下面是C1，C2，C3，C4各自的类定义。


```java
@Data
@EqualsAndHashCode(callSuper=true)
@NoArgsConstructor
@AllArgsConstructor
public class C1 extends TestChoice {
	private int a;
}
```


```java
@Data
@EqualsAndHashCode(callSuper=true)
@NoArgsConstructor
@AllArgsConstructor
public class C2 extends TestChoice {
	private double a;
}
```

```java
@Data
@EqualsAndHashCode(callSuper=true)
@NoArgsConstructor
@AllArgsConstructor
public class C3 extends TestChoice {
	private Location a;
}
```

```java
@Data
@EqualsAndHashCode(callSuper=true)
@NoArgsConstructor
@AllArgsConstructor
public class C4 extends TestChoice {
	private String a;
}
```

如果一个设备的属性的数据类型是上述的任意类型，对这个属性的读取和设置的程序如下所示，可以设置属性为C4类型的值，也可以C1，C2或者C3。

```java
//读取TestChoice任意类型属性
TestChoice value = session.get(deviceId, attribute, TestChoice.class);
//设置TestChoice任意类型中C4类型属性
C4 c4 = new C4(str);
session.set(deviceId, attribute, c4);
```

