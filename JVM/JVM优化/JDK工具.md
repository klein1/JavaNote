## JDK 命令行工具

 JDK 安装目录下的 bin 目录下：

- **`jps`** (JVM Process Status）：查看所有 Java 进程（启动类、全类名`-l`、传入参数`-m`、 JVM参数`-v`）；
- **`jstat`**（ JVM Statistics Monitoring Tool）：监视虚拟机各种运行状态信息`jstat -<option> [-t] [-h<lines>] <vmid> [<interval> [<count>]]`；
- **`jinfo`** (Configuration Info for Java)：实时地查看和调整虚拟机各项参数`jinfo -flag [+|-] name vmid`；
- **`jmap`** (Memory Map for Java)：生成堆转储快照；
- **`jhat`** (JVM Heap Dump Browser) ：分析堆转储快照（HTTP服务器查看）;
- **`jstack`** (Stack Trace for Java)：生成线程快照，线程快照就是当前虚拟机内每一条线程正在执行的方法堆栈的集合（线程间死锁、死循环、请求外部资源导致的长时间等待）。



## JDK 可视化分析工具

### jconsole：Java 监视与管理控制台

查看 Java 程序概况

内存监控

线程监控

![image.png](https://upload-images.jianshu.io/upload_images/9229344-59cf1190373141ad.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)