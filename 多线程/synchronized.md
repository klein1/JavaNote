### 三种使用方式

- **修饰实例方法，作用于当前对象实例加锁，进入同步代码前要获得当前对象实例的锁**。
- **修饰静态方法，作用于当前类对象加锁，进入同步代码前要获得当前类对象的锁** 。
- **修饰代码块，指定加锁对象，对给定对象加锁，进入同步代码块前要获得给定对象的锁。**



**① synchronized 同步语句块的情况**

**monitorenter 和 monitorexit 指令，其中 monitorenter 指令指向同步代码块的开始位置，monitorexit 指令则指明同步代码块的结束位置。** 当执行 monitorenter 指令时，线程试图获取锁也就是获取 monitor(monitor对象存在于每个Java对象的对象头中，synchronized 锁便是通过这种方式获取锁的，也是为什么Java中任意对象可以作为锁的原因) 的持有权。当计数器为0则可以成功获取，获取后将锁计数器设为1也就是加1。相应的在执行 monitorexit 指令后，将锁计数器设为0，表明锁被释放。如果获取对象锁失败，那当前线程就要阻塞等待，直到锁被另外一个线程释放为止。

**② synchronized 修饰方法的的情况**

**ACC_SYNCHRONIZED 标识**，该标识指明了该方法是一个同步方法，JVM 通过该 ACC_SYNCHRONIZED 访问标志来辨别一个方法是否声明为同步方法，从而执行相应的同步调用。



监视器锁（monitor）是依赖于底层的操作系统的 Mutex Lock 来实现的，Java 的线程是映射到操作系统的原生线程之上的。如果要挂起或者唤醒一个线程，都需要操作系统帮忙完成，而操作系统实现线程之间的切换时需要从用户态转换到内核态，这个状态之间的转换需要相对比较长的时间，时间成本相对较高，这也是为什么早期的 synchronized 效率低的原因。



### Synchronized 和 ReenTrantLock 的对比

**① 两者都是可重入锁**

自己可以再次获取自己的内部锁。

**② synchronized 依赖于 JVM 而 ReenTrantLock 依赖于 API**

synchronized 是依赖于 JVM 实现的，虚拟机团队在 JDK1.6 为 synchronized 关键字进行了很多优化，但是这些优化都是在虚拟机层面实现的，并没有直接暴露给我们。ReenTrantLock 是 JDK 层面实现的（也就是 API 层面，需要 lock() 和 unlock 方法配合 try/finally 语句块来完成），所以我们可以通过查看它的源代码，来看它是如何实现的。

**③ ReenTrantLock 比 synchronized 增加了一些高级功能**

- **中断等待锁的线程的机制**。

  通过`lock.lockInterruptibly()`来实现这个机制。

- **ReenTrantLock可以指定是公平锁还是非公平锁，而synchronized只能是非公平锁。**

  通过 ReenTrantLock类的`ReentrantLock(boolean fair)`构造方法来制定是否是公平的。

- **可实现选择性通知（锁可以绑定多个条件）。**

  synchronized关键字相当于整个Lock对象中只有一个Condition实例，所有的线程都注册在它一个身上。如果执行notifyAll()方法的话就会通知所有处于等待状态的线程这样会造成很大的效率问题，而Condition实例的signalAll()方法 只会唤醒注册在该Condition实例中的所有等待线程。

**④ 性能已不是选择标准**

JDK1.6 之后，synchronized 和 ReenTrantLock 的性能基本持平。优化后的synchronized和ReenTrantLock一样，在很多地方都是用到了CAS操作。