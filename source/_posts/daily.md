---
title: 日常记录
tags:
  - 2022
  - 记录
categories: 技术
cover: >-
  https://pic1.zhimg.com/80/v2-1e7bd042df73e47bb951e70b298c96ca_1440w.webp?source=1940ef5c
abbrlink: 535d1ea3
date: 2022-12-28 17:55:54
---

基于uv、pv、白名单、ab实验、正交	

## 12.12

1、今天学习了两个小时

2、看完了美团线程池的文章，以及线程池实现原理的文章

https://blog.csdn.net/zhengzhaoyang122/article/details/110789385、https://www.cnblogs.com/hanease/p/15869691.html、

 https://www.zhihu.com/question/485071288/answer/2468999501

3、明天看concurrentHashMap的实现原理

## 12.11

1、今天学习了3小时

2、看了AQS的应用的文章、了解了线程池的核心参数和类型

https://blog.51cto.com/u_15659694/5733637、https://tech.meituan.com/2020/04/02/java-pooling-pratice-in-meituan.html

3、看完美团关于线程池的文章，熟悉线程池的实现原理

## 12.10

1、今天学习了4小时

2、看了AQS的实现原理和部分源码，基本理解了AQS的加锁原理，了解了公平锁和非公平锁的实现原理

https://segmentfault.com/a/1190000017372067、https://www.cnblogs.com/wang-meng/p/12816829.html、https://juejin.cn/post/6844903895622221832

3、看并发包下对于AQS的应用

## 12.9

1、今天学习了两个小时

2、看了美团关于AQS的解析文章、看了一些阻塞队列的实现和使用

https://blog.csdn.net/qq_37774171/article/details/122742494、https://www.jianshu.com/p/4fae4c051111

3、看AQS的实现原理、总结并发的知识点输出

## 12.8

1、今天学习了两个半小时

2、看了futuretask中的装饰者模式的应用、看了一些aqs的文档、研究了chatGPT的应用

https://blog.csdn.net/zxc123e/article/details/89684419、https://tech.meituan.com/2019/12/05/aqs-theory-and-apply.html、

https://juejin.cn/post/6844903895622221832

3、看美团关于AQS的文章，和并发包下的一些类

2022年12月7日23:31:13
作用、cas、装饰者模式、并发包、线程池、线程复用、池化思想、blockQueue、算法题

## 12.7

1、今天学习了一个小时

2、主要看了futuretask的源代码和原理解析

http://events.jianshu.io/p/18eced78038a

3、明天看完CAS和装饰者模式的应用设计

## 12.6

1、今天学习了1小时

2、看了CompletableFuture的实现

通过链表来完成任务的回调，依赖处理。每个回调方法对应一个CompletableFuture, 如果上一个

CompletableFuture未完成，则将当前CompletableFuture添加到上一个对象的栈属性中，任务执行完毕后，回调栈中的Completion方法

https://blog.csdn.net/PNGYUL/article/details/119838961

3、通过源码debug查看任务间的依赖关系理解执行过程

## 12.5

1、今天学习了1小时

2、看了一些CompletableFuture的源码，和一些api接口的设计，写了CompletableFuture的任务运行demo

runAsync、supplyAsync，thenApply和thenApplyAsync等

异步回调处理的接口类似，使用thenApply时子任务与父任务使用的是同一个线程，thenApplyAsync在子任务中可能是另起一个线程执行任务，并且thenRunAsync可以自定义线程池，默认的使用ForkJoinPool.commonPool()

组合任务处理；

thenCombine、thenAcceptBoth 和runAfterBoth，组合的两个任务都成功才进行下面的任务，thenCombine有返回值

applyToEither、acceptEither和runAfterEither 组合的两个任务有一个成功就进行下面的任务 applyToEither有返回值

allOf / anyOf  所有的任务都执行完返回null，任意任务执行完get时会抛异常，全执行完返回结果

3、深入理解CompletableFuture的异步实现原理，多看源代码实现



## 12.4

1、今天学习了4个小时

2、看完了美团关于CompletableFuture的技术文章，以及回调地狱的产生和解决，看了CAS的实现原理

回调基于观察者模式和CAS通过栈的方式调用完成。CompletableFuture的接口传入参数包含函数式的接口，后续通过CompletableFuture和Completion入栈弹栈

额外说明

- CompletableFuture还实现了CompletionState的一些接口
  - 当CompletableFuture任务完成后，同步是用任务执行线程来执行依赖任务结果的函数或者行为
  - 所有异步的方法在没有显示指定executor参数的情况下都是复用ForkJoinPool.commonPool()线程池来执行
  - 所有CompletionState方法的实现都是相互独立的，以便一个方法的行为不会因为重载了其他方法而受影响
- 一个ComletableFuture任务可能有一些依赖其计算结果的行为方法，这些行为方法被手机到一个无锁基于CAS操作的链接起来的链表组成的栈中；当CompletableFuture的计算任务完成后，会自动弹出栈中的行为方法并执行

https://www.jianshu.com/p/31d17fc56484、

3、结合代码实现继续看CompletableFuture的实现原理，写任务处理的demo

## 12.3

1. 今天学习了一个半小时

2. 主要看了美团的技术文章和线程间的等待和唤醒、CompletableFuture的原理还是没理解需要继续花时间看，

   ​	https://blog.csdn.net/weixin_42480780/article/details/115904832、https://zhuanlan.zhihu.com/p/515993095

3. 继续看美团 CompletableFuture原理与实践 文章，理解CompletableFuture的实现原理，包括回调地狱问题

## 12.2

1. 今天学习了一个半小时
2. 看了awaitDone的实现过程、
   1. 如果线程被中断了，移除节点，抛出异常
   2. 如果状态大于COMPLETING，那么直接返回
   3. 如果状态是COMPLETING，在set和setException可以看到，处于COMPLETING是一个暂时状态，很快就会进入下一个状态，所以这儿就调用了Thread.yield()方法让步一下
   4. 如果状态是NEW且节点为null，那么创建一个节点
   5. 如果还没有将当前线程加入队列，那么将当前线程加入到等待队列中。由于WaitNode是一个单链表结构，FutureTask中保存了waiters的变量，就可以沿着该变量得到所有等待的线程
   6. 如果限制了时间，那么计算出生出超出时间，挂起指定时间。当解除挂起时，如果计算还未完成，那么将会由于没有时间了，调用removeWaiter方法移除节点。
   7. 如果没有限制时间，那么将线程无限挂起
3. completablefuture的实现原理，回顾整理扩展点和future的说辞

## 12.1

1、今天学习了三个小时

2、类实现了BeanPostProcessor接口，在Bean对象在实例化和[依赖注入完毕后，每个类在初始化的前后都会执行前后扩展点的方法，可以在前后加入扩展。类继承了initializingBean接口，此类会在bean的属性初始化后会执行该方法（当前类只执行一次），实现 `Aware` 接口用于让 `bean` 能拥有某些额外的感知能力	。实现了Aware接口的bean在被初始化之后，可以把对应的资源通过set方法装配进去（获取对应资源 BeanNameAware：注入bean的名字 BeanFactoryAware：注入BeanFactory容器 ApplicationContextAware：注入ApplicationContext容器）进行后续操作

https://blog.csdn.net/qq_46127735/article/details/111034714

3、明天看懂futuretask的cas和阻塞队列和LockSupport，串联get方法处理过程

## 11.30

1、今天学习了一个半小时

2、主要是串联前面的知识点、看awaitDone的实现原理

ApplicationContext的BeanFactory 的[子类](https://so.csdn.net/so/search?q=子类&spm=1001.2101.3001.7020)，ApplicationContext可以在服务器启动的时候自动实例化所有的bean,而 BeanFactory只有在调用getBean()的时候才去实例化那个bean

InitializingBean 继承该接口的类，在初始化bean的时候会执行该方法

在Spring容器的创建过程中每一个bean对象的初始化方法（具体为Bean初始化前后）会回调BeanPostProcessor中定义的两个方法调用之前回调

3、看completablefuture的实现原理

## 11.29

1. 今天学习了一个半小时
2. 看了CompletableFuture的使用和api、以及一些实现原理    主要是异步回调实现任务编排                                                                                                                                                                                                                                                                                                 https://blog.csdn.net/sermonlizhi/article/details/123356877、https://www.jianshu.com/p/abfa29c01e1d、https://www.cnblogs.com/ludongguoa/p/15316488.html
3. 写线程间通信的demo和CompletableFuture调用的demo，知识点串联准备

## 11.28

1、今天学习了一个半小时

2、看了线程间的通信机制，等待唤醒机制wait、notify、notifyAll，共享内存volatile 关键字、辅助类（CountDownLatch、CyclicBarrier、Semaphore），

锁机制 LockSupport.park 与 LockSupport.unpark、ReentrantLock + Condition、

https://zhuanlan.zhihu.com/p/362772704、https://blog.csdn.net/h380115990/article/details/110439709、https://blog.csdn.net/weixin_53812805/article/details/124532640

3、看futuretask中运用的装饰者模式和了解computablefuture实现思想

## 11.27

1、今天学习了4小时

2、看了futureTask关于awaitDone的源码，了解其实现原理。看了spring生命周期中的扩展点及其用法区别。看了线程的几种状态和状态间的转换

不断轮询查看FutureTask的状态。在get阻塞期间：

执行get的线程被中断，移除FutureTask的所有阻塞队列中的线程（waiters）,并抛出中断异常；FutureTask的状态转换为完成状态（正常完成或取消），则返回完成状态；FutureTask的状态变为COMPLETING, 则说明正在set结果，此时让线程等一等；FutureTask的状态为初始态NEW，则将当前线程加入到FutureTask的阻塞线程中去；get方法没有设置超时时间，则阻塞当前调用get线程；如果设置了超时时间，则判断是否达到超时时间，如果到达，则移除FutureTask的所有阻塞列队中的线程，并返回此时FutureTask的状态，如果未到达时间，则在剩下的时间内继续阻塞当前线程。

New（新创建）Runnable（可运行）Blocked（被阻塞）Waiting（等待）Timed Waiting（计时等待）Terminated（被终止）

​	https://blog.csdn.net/codershamo/article/details/51901057、https://blog.csdn.net/qq_38826019/article/details/117389466、https://zhuanlan.zhihu.com/p/266709645

3、明天了解线程间的通信机制和实现原理、重写spring的扩展点代码



本周目标：

futuretask怎么运用装饰者模式、
线程状态、转换
线程间通信
await

线程池、线程复用、池化思想
computablefuture实现思想
aqs

## 11.26

1、学习了一个小时

2、主要juc并发包中锁的使用，volatile、synchronized等关键字及内存模型原子性可见性有序性

https://www.cnblogs.com/zhongqifeng/p/14684028.html、https://blog.csdn.net/weixin_36759405/article/details/83034386

3、了解aqs的队列和锁实现原理

## 11.25

1、今天学习了两个小时

2、aqs的实现原理、volatile 关键字+ CAS 比较和交换+ 一个虚拟的FIFO双向队列、排它锁和共享锁

AQS采用了一个int类型的互斥变量state，0表示没有任务线程使用该资源，而大于等于1表示已经有线程正在持有锁资源。一个线程获取锁资源的时候，会判断state是否等于0（无锁状态），如果是，则把这个state更新为1，表示占用到锁，而这个过程中，如果多个线程同时做这样的操作，就会导致线程的安全性问题。因此AQS采用了CAS机制，来保证互斥变量state更新的原子性。未获得到锁的线程通过Unsafe类中的park方法去进行阻塞，把阻塞的线程按照先进先出的原则去放到一个双向链表的结构中，当获得所得线程释放锁之后，会从这个双向链表的头部去唤醒下一个等待的线程再去竞争锁。

https://www.cnblogs.com/hanease/p/14897445.html、https://zhuanlan.zhihu.com/p/377412161、https://blog.csdn.net/lzh804121985/article/details/124143761

3、明天回顾本周所学的知识点，串联准备明天的讲解输出

## 11.24

1、今天学习了一个小时

2、jdk和cglib的主要区别，jdk是反射机制生成一个实现代理接口的匿名类，在调用具体方法前调用InvokeHandler来处理 ，所以jdk被代理的对象必须实现接口，cglib采用asm字节码框架动态修改字节码生成子类，若 目标对象实现了接口默认使用jdk动态代理、

jdk代理类和目标类都实现了同样的接口，InvocationHandler持有目标类，代理类委托InvocationHandler去调用目标类的原始方法 

cglib代理的代理类继承了目标类并重写了目标方法，通过回调函数MethodInterceptor调用父类方法执行原始逻辑

静态代理只能手动完成代理，动态代理可以运行时动态生成代码，没有代理类的扩展限制

3、明天看coccurrent并发包文档，了解AQS的实现原理

## 11.23

1、今天学习了一个半小时

2、熟悉了三级缓存关于aop代理类的解决方案、写了一道算法题整数反转、看了几篇动态代理的文档

https://www.cnblogs.com/xujq/p/16283608.html、https://blog.csdn.net/buyaoshuohua1/article/details/78923773、https://blog.csdn.net/qq_46494427/article/details/124173617

3、明天继续看jdk和cglib的代理、了解其代理的实现机制和区别

## 11.22

1、今天学习了两小时

2、写完了三级缓存和扩展点的代码、看了部分文档了解了三级缓存的原理、

https://blog.csdn.net/m0_67401417/article/details/125244712、https://zhuanlan.zhihu.com/p/496273636

3、三级缓存关于aop代理的部分还有点不明白，明天看完，以及spring的aop动态代理熟悉原理

## 11.21

1、今天学习了两小时

2、看了部分futuretask的源码，理解了get返回值的原理，其中涉及到UNSAFE的状态转换不是很明白。其中的compareAndSwapObject就是CAS

https://blog.csdn.net/CsWarmSun/article/details/122274555，主要源码实现如下，创建futuretask时把callable和result提交到runnable中，后续start执行时调用call方法执行获取结果

```java
private int awaitDone(boolean timed, long nanos)
        throws InterruptedException {
        final long deadline = timed ? System.nanoTime() + nanos : 0L;
        WaitNode q = null;
        boolean queued = false;
        for (;;) {
            if (Thread.interrupted()) {
                removeWaiter(q);
                throw new InterruptedException();
            }

            int s = state;
            if (s > COMPLETING) {
                if (q != null)
                    q.thread = null;
                return s;
            }
            else if (s == COMPLETING) // cannot time out yet
                Thread.yield();
            else if (q == null)
                q = new WaitNode();
            else if (!queued)
                queued = UNSAFE.compareAndSwapObject(this, waitersOffset,
                                                     q.next = waiters, q);
            else if (timed) {
                nanos = deadline - System.nanoTime();
                if (nanos <= 0L) {
                    removeWaiter(q);
                    return state;
                }
                LockSupport.parkNanos(this, nanos);
            }
            else
                LockSupport.park(this);
        }
    }
```



3、三级缓存原理理解，编码实现

## 11.20

1、今天学习了五小时

2、spring注解重新抽取了代码，增加了二级缓存和bean注入，方法间的颗粒度不够后面再优化。写了装饰者模式的demo、像servlet和BeanFactory都用到了装饰者模式，可以更好的动态拓展功能，一般采用抽象类的方式，比起接口的单继承，抽象类可以多实现

https://blog.51cto.com/learningfish/5387281、https://zhuanlan.zhihu.com/p/421998141

看了一部分futuretask的文档

当FutureTask处于未启动或者已启动的状态时，调用FutureTask对象的get方法会将导致调用线程阻塞。当FutureTask处于已完成的状态时，调用FutureTask的get方法会立即放回调用结果或者抛出异常。主要通过任务状态来判断

https://blog.csdn.net/qq_39654841/article/details/90631795、https://blog.csdn.net/qq_40685275/article/details/99838677、https://blog.csdn.net/CsWarmSun/article/details/122274555

3、明天完成三级缓存的理解，在现有代码上体现，futuretask的返回值和回调原理理解

## 11.19

1、今天学习了四个半小时，开会两个半小时

2、整理了自己的上周知识并归纳输出，看了java并发包，

并发包主要包含以下核心类，主要使用锁机制并发问题

锁机制类Locks : Lock, Condition, ReentrantLock, ReadWriteLock,LockSupport

原子操作类 Atomic : Atomiclnteger,AtomicLong,LongAdder  主要保证原子性

线程池相关类Executor : Future, Callable, Executor,ExecutorService 

信号量三组工具类Tools : CountDownLatch, CyclicBarrier,Semaphore

并发集合类Collections : CopyOnWriteArrayList, ConcurrentHashMap

https://www.cnblogs.com/hanease/p/15893075.html

https://blog.csdn.net/tianwailaikewbb/article/details/120589084

AbstractQueuedSynchronizer抽象队列同步器 AQS

https://www.jianshu.com/p/64089fe37fc5

https://blog.csdn.net/weixin_41818733/article/details/115640256

3、明天完成对于spring注解方法的拆分以及bean注入、其他注解和扩展的接口实现的编码，写一个装饰器模式的demo，看一些futuretask的文档

## 11.15

1. 今天学习了一个半小时
2. 写完了合并链表的算法题，bean的生命周期：bean创建-->初始化-->销毁 的过程  https://blog.csdn.net/weixin_45723046/article/details/124546319

```java
 https://www.cnblogs.com/misscai/p/14749225.html
 Spring 对bean 进行实例化。
  Spring 将值和bean的引用注入到bean对应的属性中。
  如果bean实现了BeanNameAware接口，Spring将bean的ID传递给setBean-Name()  方法。
  如果bean 实现了BeanFactoryAware接口，Spring将调用setBeanFactory() 方法，将BeanFactory容器实例传入。
  如果bean实现了ApplicationContextAware接口，Spring将调用setApplicationContext() 方法，将bean所在的应用上下文的引用传入进来。
  如果bean实现了BeanPostProcessor接口，Spring将调用它们的post-ProcessBeforeInitialization() 方法
  如果bean实现了InitializingBean接口，Spring将调用它们的after-PropertiesSet()方法。类似的，如果bean使用init-method声明了初始化方法，该方法也会被调用。
  如果bean实现了BeanPostProcessor接口，Spring将调用它们的post-ProcessAfterInitialization() 方法。
  此时, bean 已经准备就绪，可以被应用程序使用了，它们将一直驻留在应用上下文中，直到该应用上下文被销毁。
  如果bean实现了DisposableBean接口，Spring将调用它的destory()接口方法。同样,如果bean使用destroy-method声明了销毁方法，该方法也会被调用。

https://www.zhihu.com/question/38597960

1.Spring对Bean进行实例化（相当于程序中的new Xx()）
2.Spring将值和Bean的引用注入进Bean对应的属性中
3.如果Bean实现了BeanNameAware接口，Spring将Bean的ID传递给setBeanName()方法（实现BeanNameAware清主要是为了通过Bean的引用来获得Bean的ID，一般业务中是很少有用到Bean的ID的）
4.如果Bean实现了BeanFactoryAware接口，Spring将调用setBeanDactory(BeanFactory bf)方法并把BeanFactory容器实例作为参数传入。（实现BeanFactoryAware 主要目的是为了获取Spring容器，如Bean通过Spring容器发布事件等）
5.如果Bean实现了ApplicationContextAwaer接口，Spring容器将调用setApplicationContext(ApplicationContext ctx)方法，把y应用上下文作为参数传入.(作用与BeanFactory类似都是为了获取Spring容器，不同的是Spring容器在调用setApplicationContext方法时会把它自己作为setApplicationContext 的参数传入，而Spring容器在调用setBeanDactory前需要程序员自己指定（注入）setBeanDactory里的参数BeanFactory )
6.如果Bean实现了BeanPostProcess接口，Spring将调用它们的postProcessBeforeInitialization（预初始化）方法（作用是在Bean实例创建成功后对进行增强处理，如对Bean进行修改，增加某个功能）
7.如果Bean实现了InitializingBean接口，Spring将调用它们的afterPropertiesSet方法，作用与在配置文件中对Bean使用init-method声明初始化的作用一样，都是在Bean的全部属性设置成功后执行的初始化方法。
8.如果Bean实现了BeanPostProcess接口，Spring将调用它们的postProcessAfterInitialization（后初始化）方法（作用与6的一样，只不过6是在Bean初始化前执行的，而这个是在Bean初始化后执行的，时机不同 )
9.经过以上的工作后，Bean将一直驻留在应用上下文中给应用使用，直到应用上下文被销毁
10.如果Bean实现了DispostbleBean接口，Spring将调用它的destory方法，作用与在配置文件中对Bean使用destory-method属性的作用一样，都是在Bean实例销毁前执行的方法。
```

明天继续学习springbean的生命周期，查看BeanNameAware、BeanFactoryAware、ApplicationContextAware等接口的源码

## 11.14

1. 今天学习了两个半小时
2. 写完了一道算法题和spring观察者模式的demo，代码已提交
3. 明天写完合并链表的算法题、写spring的autowired注解和bean注解、看文档输出bean的生命周期

## 11.13

1. 今天学习了4小时
2. 写完了策略模式和观察者模式的demo、java.util包中，提供了Observable类以及Observer接口，在此基础上可以实现观察者模式但效率较低 https://segmentfault.com/a/1190000040530952  观察者模式是一种对象行为模式，可用于发布订阅等场景，将目标与观察者之间解耦。component注解类中的autowired后面不知道怎么写了，
3. 明天完成无重复子串的算法题，了解滑动窗口的原理，写spring中事件监听器实现观察者模式的demo

## 11.12

1. 今天学习了四个半小时

2. 主要是写了spring的componentScan、component、autowired注解，碰到了很多问题，写的很困难    参考文档：https://www.zhihu.com/question/417421318/answer/2503989509、https://blog.csdn.net/weixin_39864738/article/details/110922688、https://blog.csdn.net/qq_42764468/article/details/124520971 

3. 看了几篇策略模式的文档，多业务场景下可以用策略模式重构代码，避免if else引起的代码复杂臃肿、策略选择多样还能灵活拓展，不影响现有的业务逻辑  https://www.jianshu.com/p/3bcf55cf83d3、https://zhuanlan.zhihu.com/p/346607652

4. 明天把component注解的对象实例化过程写完，包括一级缓存和二级缓存、autowired注入，多重if、else的策略模式demo

   

## 11.09

今天学了两个小时，开会开了两个小时

函数式编程

串行流：list.stream()

并行流：list.parallelStream()

https://www.shuzhiduo.com/A/QW5Y3RQGzm/

https://blog.csdn.net/qq_58148854/article/details/125584008

```java
Collector 是专门用来作为 Stream 的 collect 方法的参数的，而 Collectors 是作为生产具体 Collector 的工具类。
功能齐全，可以用来分组等操作、其中有些方法也可以用函数式编程的流式处理
https://blog.csdn.net/V539413949/article/details/124516374、https://blog.csdn.net/qq_43842093/article/details/122136492
Collector 用于合并 Stream 的元素处理结果
forEach：该方法用于对 Stream 中的每个元素进行迭代操作
map：该方法用于将每个元素映射到对应的结果上,返回的是结果的流
filter：该方法用于过滤满足条件的元素
IntSummaryStatistics 统计工具 ： 求最大值、最小值、和、平均数
```

明天完成spring的component开发和继续前面未完成的计划

## 11.08

今天学习了三小时，主要是看了stream流和函数式接口

Stream流：java8新特性，以函数式编程的方式操作集合

https://zhuanlan.zhihu.com/p/533692264

https://zhuanlan.zhihu.com/p/339038230

https://blog.csdn.net/ss810540895/article/details/126172285

可以通过一系列的流处理集合数据、得到最终想要的结果、中间的流式处理只会形成流，不回处理结果，

先在管道中创建一系列的流，在新流上调用终端操作，再执行中间的流处理逻辑，且流只能被调用一次

平常使用较多的场景是排序、数据转换、筛选

常见函数：java.util.function包下的接口

Function函数  传入一个参数T，返回一个参数R

Predicate函数 	传入一个参数T，返回boolean

Consumer函数 传入一个参数T，返回空

Optional接口，允许返回空对象，避免空指针产生，可以更好地转换对象值，内置的方法也能过滤数据

https://www.jdon.com/idea/java/using-optional-effectively-in-java-8.html

https://juejin.cn/post/6844903960050925581

Optional作为中间的数据转换，可以更好的避免空指针和处理数据

明天写完，观察者和策略模式demo，3道算法题提交，思考spring扩展点的实现

## 11.06

今天学了4小时、看了S12全球总决赛、开会3.5小时

写了无重复最长子串、合并有序链表的算法题

看了一些循环依赖的文档：

https://www.zhihu.com/question/438247718/answer/1730527725

https://zhuanlan.zhihu.com/p/151392267

循环依赖是指多个对象之间的依赖形成了闭环，从而导致循环依赖

循环依赖的解决方法是提前暴露，除了bean的map作为一级缓存，可以用二级缓存和三级缓存来解决循环依赖问题

看了一点源码，还是没有理解透，后面要继续花时间，

```java
protected Object getSingleton(String beanName, boolean allowEarlyReference) {
		// Quick check for existing instance without full singleton lock
    	//从一级缓存singletonObjects中获取是否存在当前bean
		Object singletonObject = this.singletonObjects.get(beanName);
    	//如果为空且正在创建的单例bean Map中存在当前bean
		if (singletonObject == null && isSingletonCurrentlyInCreation(beanName)) {
            // 从二级缓存earlySingletonObjects获取已经实例化的Bean
			singletonObject = this.earlySingletonObjects.get(beanName);
            // 如果没有实例化的Bean， 但是参数allowEarlyReference为true
			if (singletonObject == null && allowEarlyReference) {
                //这个地方为什么要锁住呢，和双检锁一样的写法
				synchronized (this.singletonObjects) {
					// Consistent creation of early reference within full singleton lock 在全单例锁中创建一致的早期引用
                    //从一级缓存singletonObjects中获取是否存在当前bean
					singletonObject = this.singletonObjects.get(beanName);
					if (singletonObject == null) {
						singletonObject = this.earlySingletonObjects.get(beanName);
						if (singletonObject == null) {
                             // 从三级缓存singletonFactories获取ObjectFactory
							ObjectFactory<?> singletonFactory = this.singletonFactories.get(beanName);
							if (singletonFactory != null) {
                                // 使用三级缓存ObjectFactory获取Bean实例
								singletonObject = singletonFactory.getObject();
                                // 保存实例， 并清理三级缓存ObjectFactory
								this.earlySingletonObjects.put(beanName, singletonObject);
								this.singletonFactories.remove(beanName);
							}
						}
					}
				}
			}
		}
		return singletonObject;
	}
```

```java
/** 维护着所有创建完成的Bean */ //一级缓存
private final Map<String, Object> singletonObjects = new ConcurrentHashMap<String, Object>(256);
/** 维护着所有半成品的Bean */ //二级缓存
private final Map<String, Object> earlySingletonObjects = new HashMap<String, Object>(16);
/** 维护着创建中Bean的ObjectFactory */ //三级缓存
private final Map<String, ObjectFactory<?>> singletonFactories = new HashMap<String, ObjectFactory<?>>(16);

// DefaultSingletonBeanRegistry 类中的属性，包含bean的三种缓存map
	private final Map<String, Object> singletonObjects = new ConcurrentHashMap<>(256);

	/** Cache of singleton factories: bean name to ObjectFactory. */
	private final Map<String, ObjectFactory<?>> singletonFactories = new HashMap<>(16);

	/** Cache of early singleton objects: bean name to bean instance. */
	private final Map<String, Object> earlySingletonObjects = new ConcurrentHashMap<>(16);

	/** Set of registered singletons, containing the bean names in registration order. */ 
	private final Set<String> registeredSingletons = new LinkedHashSet<>(256);

	/** Names of beans that are currently in creation. */ //正在创建中的bean集合
	private final Set<String> singletonsCurrentlyInCreation =
			Collections.newSetFromMap(new ConcurrentHashMap<>(16));
```

spring解决循环依赖的过程，图上写出来理解很简单，但是要讲清晰还是不到位

![img](https://pic1.zhimg.com/80/v2-1e7bd042df73e47bb951e70b298c96ca_1440w.webp?source=1940ef5c)

计划明天把观察者模式demo写完、有效的括号算法写完、spring实现ioc的demo写完



## 11.05

今天学了两个小时，下午出去玩了，晚上回来休息了，看了下考试的题目，确实很难，侧面反映就业环境卷

【我在德国写代码-沉浸式体验程序员国外求职&肉翻干货指南【码农求职路】】 https://www.bilibili.com/video/BV1dt4y1w77u/?share_source=copy_web&vd_source=f8b1da795bc0701ef95e1892ee677d16

star法则、

延时队列：

https://blog.csdn.net/ChineseSoftware/article/details/123330873

https://blog.csdn.net/itguangit/article/details/107255368

看了下其中的api接口，新代码提交到studydemo，但每次请求都会创建一个线程，需优化。调试了很多次都没有满意的方案

## 11.04

除了上班，今天花了两个半小时学习，

【三年经验 某蚁外包，项目只会CRUD，听我建议直接跳槽18K【Java面试】实录程序员】 https://www.bilibili.com/video/BV1uP4y1U7sw/?p=2&share_source=copy_web&vd_source=f8b1da795bc0701ef95e1892ee677d16

面试应该要有自信，不能表现出自己很菜，沟通表达要专业



spring中的bean都是默认单例的，可通过设置scope=protorype来配置成多例 、singleton,protorype, request,session,global session @Scope(value = ConfigurableBeanFactory.SCOPE_PROTOTYPE)  单例优点降低了实例创建和销毁所占用的资源，缺点线程共享一个实体，会发生线程安全问题。

多例线程之间数据隔离，所以不会有线程安全问题，但是频繁的实例创建和销毁会带来资源的大量浪费。



https://vuepress.mirror.docker-practice.com/introduction/ docker go语言实现

操作系统层面的虚拟化，对进程隔离、镜像好比类，容器类似实例、有封装隔离特性、dockerfile构建镜像、from指定基础镜像、

docker目前只能构建镜像，不能对环境变量等配置进行控制。。

如果容器IP重启一直变需要用固定的ip启动容器、

docker和虚拟机的区别，docker compose.yml是什么，感觉现在都会用docker-compose的方式

https://blog.csdn.net/qq_37768368/article/details/120583141

https://zhuanlan.zhihu.com/p/387840381

docker compose -p 可在多项目直接切换，且环境隔离，符合主流使用习惯，应该是以后的潮流，现在我们新项目也都要求docker compose部署了 ，这块还没玩过，感觉挺好用的 

todo 

今天在公司用了下延时队列实现业务，但是存在一个问题，这种写法队列里本来应该有多个任务执行的，后面打印日志发现只会有一个任务执行

```java
public void delayEndRecord(String data, int num) {
    RobotRecordDelay delay = new RobotRecordDelay(num, data, num, TimeUnit.SECONDS);
    if(queue.size() > 0){
        Iterator<RobotRecordDelay> iterator = queue.iterator();
        while (iterator.hasNext()){
            RobotRecordDelay recordDelay = iterator.next();
            if(recordDelay.getData().equals(delay.getData())){
                if(queue.remove(recordDelay)){
                    queue.put(delay);
                }
            }
        }
    } else {
        queue.put(delay);
    }

    Thread thread = new Thread(()->{
        while (queue.size() != 0) {
            //取队列头部元素是否过期
            RobotRecordDelay task = queue.poll();
            if (task != null) {
                log.info("录制:{}被取消, 取消时间:{}", JSONObject.toJSONString(task), LocalDateTime.now().format(DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss")));
            }
        }
    });
    thread.start();
}
```



三个算法题忘记怎么写了，看了一遍思路，明天刷掉
