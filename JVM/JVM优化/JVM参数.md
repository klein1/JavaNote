## 堆内存相关

### 堆内存`–Xms`和`-Xmx`：

```java
-Xms<heap size>[unit] //最小
-Xmx<heap size>[unit] //最大
```

- **heap size** 表示要初始化内存的具体大小。
- **unit** 表示要初始化内存的单位。单位为***“ g”*** (GB) 、***“ m”***（MB）、***“ k”***（KB）。

```java
-Xms2G -Xmx5G // 最小2GB和最大5GB的堆内存大小
```



### 新生代内存：

```java
-XX:NewSize=<young size>[unit] //最小
-XX:MaxNewSize=<young size>[unit] //最大
-Xmn<young size>[unit]
-XX:NewRatio=<int> // 设置新生代和老年代内存的比值
```

```java
// 最小256m的内存，最大1024m的内存
-XX:NewSize=256m
-XX:MaxNewSize=1024m

// 设置256m的内存（NewSize与MaxNewSize一致）
-Xmn256m 
    
// 设置新生代（包括Eden和两个Survivor区）与老年代的比值为1:1，新生代占整个堆栈的1/2。
-XX:NewRatio=1
```



### 元空间：

```java
-XX:MetaspaceSize=N //设置 Metaspace 的初始（和最小大小）
-XX:MaxMetaspaceSize=N //设置 Metaspace 的最大大小，如果不指定大小的话，随着更多类的创建，虚拟机会耗尽所有可用的系统内存。
```



## 垃圾收集相关

### 垃圾回收器

JVM具有四种类型的*GC*实现：

- 串行垃圾收集器
- 并行垃圾收集器
- CMS垃圾收集器
- G1垃圾收集器

可以使用以下参数声明这些实现：

```java
-XX:+UseSerialGC
-XX:+UseParallelGC
-XX:+UseParNewGC
-XX:+UseG1GC
```



### GC记录

为了严格监控应用程序的运行状况，我们应该始终检查JVM的**垃圾回收**性能。最简单的方法是以人类可读的格式记录*GC*活动。

使用以下参数，我们可以记录*GC*活动：

```java
-XX:+UseGCLogFileRotation 
-XX:NumberOfGCLogFiles=< number of log files > 
-XX:GCLogFileSize=< file size >[ unit ]
-Xloggc:/path/to/gc.log
```

