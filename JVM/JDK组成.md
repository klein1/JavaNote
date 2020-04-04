#### Java开发环境：JDK（Java Development Kit）

bin：可执行程序（javac编译器、java运行工具、javadoc文档生成工具、jar打包工具等）

db：纯java实现的开源dbms

jre：运行环境

include：引入C语言头文件（JDK通过C、C++实现）

lib：java类库（供JDK使用，工具）



#### Java运行环境：JRE（Java Runtime Environment）

bin：可执行程序（等同于 jdk/bin）、DLL

lib：java类库（供JVM使用，含标准类库、扩展类）

​		rt.jar：Bootstrap类（构成Java平台核心API的运行时类）

​		charsets.jar：字符转换类

​		ext：扩展程序



### Oracle JDK 和 OpenJDK 的对比

- OpenJDK 项目主要基于 Sun 捐赠的 HotSpot 源代码，完全开源；
- Oracle JDK 是 OpenJDK 的一个实现，并不是完全开源的（含商业功能）；
- Oracle JDK 比 OpenJDK 更稳定，响应性和 JVM 性能方面更好；