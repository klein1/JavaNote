## BigDecimal

```java
float a = 1.0f - 0.9f;
float b = 0.9f - 0.8f;
System.out.println(a);// 0.100000024
System.out.println(b);// 0.099999964
System.out.println(a == b);// false
```

> 浮点数之间的等值判断，基本数据类型不能用==来比较，包装数据类型不能用 equals 来判断。



##### 使用 BigDecimal 来定义浮点数的值，再进行浮点数的运算操作

```java
BigDecimal a = new BigDecimal("1.0");
BigDecimal b = new BigDecimal("0.9");
BigDecimal c = new BigDecimal("0.8");
BigDecimal x = a.subtract(b);// 0.1
BigDecimal y = b.subtract(c);// 0.1
System.out.println(x.equals(y));// true 
```

##### 大小比较

```java
// 返回 -1 表示小于，0 表示 等于， 1表示 大于
BigDecimal a = new BigDecimal("1.0");
BigDecimal b = new BigDecimal("0.9");
System.out.println(a.compareTo(b));// 1
```

##### 保留几位小数

```java
BigDecimal m = new BigDecimal("1.255433");
BigDecimal n = m.setScale(3,BigDecimal.ROUND_HALF_DOWN);
System.out.println(n);// 1.255
```

##### 使用注意事项

为了防止精度丢失，推荐使用 **BigDecimal(String)** 构造方法来创建对象。

BigDecimal 主要用来操作（大）浮点数，BigInteger 主要用来操作大整数（超过 long 类型）。

BigDecimal 的实现利用到了 BigInteger，所不同的是 BigDecimal 加入了小数位的概念

