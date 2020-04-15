## Java 中 IO 流划分

- 按照流的流向分，可以分为输入流和输出流；
- 按照操作单元划分，可以划分为字节流和字符流；
- 按照流的角色划分为节点流和处理流。



### 按操作方式分类结构图：

![image.png](https://upload-images.jianshu.io/upload_images/9229344-15a36cee5f170950.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

### 按操作对象分类结构图：

![image.png](https://upload-images.jianshu.io/upload_images/9229344-10bd59a2db388f95.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



### 既然有了字节流,为什么还要有字符流?

问题本质想问：**不管是文件读写还是网络发送接收，信息的最小存储单元都是字节，那为什么 I/O 流操作要分为字节流操作和字符流操作呢？**

回答：字符流是由 Java 虚拟机将字节转换得到的，问题就出在这个过程还算是非常耗时，并且，如果我们不知道编码类型就很容易出现乱码问题。所以， I/O 流就干脆提供了一个直接操作字符的接口，方便我们平时对字符进行流操作。如果音频文件、图片等媒体文件用字节流比较好，如果涉及到字符的话使用字符流比较好。