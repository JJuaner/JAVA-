
### Sychronized和Lock区别
Sychronized和Lock都是Java提供的锁机制

    synchronized是java关键字，属于JVM层面
    lock系列锁是一系列接口/类，位于JUC下，属于jdk-api层面

相同点在于两者都是`独占锁`和`可重入锁`

    sync加锁解锁过程是由jvm自动管理，对程序员透明
    lock锁需要程序员手动进行加锁解锁
    sync通过object类的wait，notify/all方法进行线程的调度 
    lock锁是通过condition的await和signal方法进行线程调度

以上只是两种锁底层实现不同造成的一些小的区别，本质还是等价的

    主要功能区别在于lock锁提供更加丰富的特性，使用起来更加灵活
    比如，Lock提供的锁不仅支持非公平锁支持公平锁，当线程获取不到锁时不一定阻塞可以通过cas重试，线程等待锁时允许响应中断，可以判断锁的状态
