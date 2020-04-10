## Arrays

1. 排序 : `sort()`
2. 查找 : `binarySearch()`
3. 比较: `equals()`
4. 填充 : `fill()`
5. 转列表: `asList()`
6. 转字符串 : `toString()`
7. 复制: `copyOf()`



#### T类型：8种基本数据类型、对象（Object）



### 排序

```java
void sort(T[] a) //按升序排列
void sort(T[] a, Comparator<? super T> cmp)
void sort(T[] a, int fromIndex, int toIndex)
void sort(T[] a, int fromIndex, int toIndex, Comparator<? super T> cmp)
void parallelSort(T[] a) //使用并行排序-合并排序算法，适用于大数据集
```



### 查找

```java
void Arrays.binarySearch(T[] a, T key); 
void Arrays.binarySearch(T[] a, int fromIndex, int toIndex, T key);
void Arrays.binarySearch(T[] a, T key, Comparator<? super T> c);
void Arrays.binarySearch(T[] a, int fromIndex, int toIndex, T key, Comparator<? super T> c);
```

#### （排序、查找中T没有boolean类型）



### 比较

```java
boolean Arrays.equals(T[] a, T[] a2)
boolean Arrays.deepEquals(Object[] a1, Object[] a2) //用于比较多维数组，equals返回false
```



### 填充

```java
void Arrays.fill(T[] a, T val)
void Arrays.fill(T[] a, int fromIndex, int toIndex, T val)
```



### 转列表

```java
List<T> Arrays.asList(T... a)
```

**传递的数组必须是对象数组，而不是基本类型。**

```java
String [] s= new String[]{
    "dog", "lazy", "a", "over", "jumps", "fox", "brown", "quick", "A"
};
List<String> list = Arrays.asList(s);
Collections.reverse(list);
s=list.toArray(new String[0]);//没有传递任何参数的话返回的是Object类型数组
```



### 转字符串

```java
String Arrays.toString(T[] a)
String Arrays.deepToString(Object[] a) //用于打印多维数组，tostring只会打印地址
```



### 复制

```java
T[] Arrays.copyOf(T[] original, int newLength)
T[] Arrays.copyOfRange(T[] original, int from, int to)
```

