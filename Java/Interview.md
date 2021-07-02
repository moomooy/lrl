面试经历的问题  

# 数据结构   

1、双向链表和单项链表  
双链表是链表的一种，由节点组成，每个数据结点中都有两个指针，分别指向直接后继和直接前驱。  
单链表只能从头结点开始访问链表中的数据元素，如果需要逆序访问单链表中的数据元素将极其低效。  

2、栈是先进后出的数据结构，
  
# MySQL  

1.当一张表上有学号成绩,另一张表上有学号姓名,怎么样连接两张表查询出不及格的同学  

首先了解主键和外键  :  
主键(primary key):主键是唯一的，用于标识一张表。
外键(foreign key):存在与外面的主键就是外键,外键可以有多个，用于建立表和表的关系。    


连接语句:  
LEFT JOIN（左连接）：返回包括左表中的所有记录和右表中连接字段相等的记录   

左连接语句:SELECT tb_student.name,tb_class.name FROM tb_student LEFT OUTER JOIN tb_class ON tb_student.classID=tb_class.id;  

RIGHT JOIN（右连接）：返回包括右表中所有记录和左表中连接字段相等的记录  

查询语句:SELECT * FROM tb_score WHERE grade> ANY(SELECT grade FROM tb_score WHERE sID=1);  

## 可以说一下事务吗  

事务四个特性(ACID):原子性，一致性，隔离性，永久性   

隔离性包括四个级别：  
read_uncommitted:最低级别，允许读取未提交的数据，造成脏读，幻读，不可重复读
read_commited：允许读取已提交的数据，阻止了脏读但还存在幻读，不可重复读
repeatable_read:可重复读，多次读取结果一致，组织脏读、不可重复读，但还存在幻读。
serlalizable：最高级别，服从ACID，依次执行，影响性能。  

2、脏读和幻读：  
脏读：发生在一个事务A读取了被另外一个事务B修改，但是还未提交的数据，加入B退回，则事务A读取的是无效的数据   
幻读：幻读发生在当两个完全相同的查询时，第二次查询所返回的结果跟第一个查询不相同

# 计算机网络  

1、三次握手：  
客户端发送SYN（SEQ=x）报文给服务器端，进入SYN_SEND状态。
服务器端收到SYN报文，回应一个SYN （SEQ=y）ACK（ACK=x+1）报文，进入SYN_RECV状态。
客户端收到服务器端的SYN报文，回应一个ACK（ACK=y+1）报文，进入Established状态。  

2、TCP 是传输控制协议，是一个可靠的面向连接的协议。  
&emsp;UDP面向非连接，不可靠，但因为不用传送许多与数据本身无关的信息，  

3、HTTP属于应用层协议，ip协议在网络层  

4、http协议2.0的多路复用  
HTTP2的请求TCP的connection一旦建立，后续请求以stream的方式发送。每个stream的基本组成单位是frame（二进制帧），每种frame又分为很多种类型例如HEADERS Frame(头部帧)，DATA Frame(内容帧)等等。请求头HEADERS Frame组成了request,返回头HEADERS Frame和DATA Frame组成了response，request和response组成了一个stream。  

5、网络404的意思：服务器找不到指定的资源，并且请求的网页不存在  

6、TCP/IP的网络模型  

有四个层次：网络接口层，网络层，传输层，应用层  
网络接口层：定义了主机间网络联通的协议  
网络层：主要用于数据的传输，路由及地址的解析，以保障主机可以把数据发送给任何网络上的目标  
传输层：使源端和目的端的机器上的对等实体可以基于会话相互通信  
应用层：负责具体应用层协议的定义，包括

# Linux  



1.怎么运用Linux查询多线程在哪个cpu上面运行  
   ps -eo ruser,pid,ppid,lwp,psr,args -L | grep qemu  
   依次在用户ID，进程ID，父进程ID，线程ID，运行该线程的CPU的序号，命令行参数（包括命令本身）  

2.怎么运用Linux查询多线程  
   ps -ef | grep  
   ps -ef:显示所有进程的消息  
   grep是查找输出包含想要的字符串的行

ls：查看文件下所有文件    
cat：查看文件内容   
touch 创建空文件   
echo创建有内容的文件   
pwd：查看当前目录   
chmod：修改权限可读，可执行  
df:列出文件系统的整体磁盘使用量   


# Java  

##  概述

### jvm,jre,jdk的关系和区别

jvm是Java虚拟机，Java程序需要运行在虚拟机上，不同的平台有自己的虚拟机，因此Java语言可以实现跨平台
jre是Java虚拟机和Java程序所需要的核心类库，核心类库主要是java.lang包，包含了运行Java程序必不可少的系统库
jdk是给Java开发人员使用的，其中包含了Java的开发工具，也包括了jre，所以安装了jdk就无需单独安装jre

### API  

常见的Java API:
java.lang.Math:提供sin，cos等类方法，PI类字段
java.util.Scanner:键盘输入到程序中
java.util.Arrays：数组类
java.util.Random:随机数生成


## 基础语法

### 局部变量和全局变量  

成员变量会被系统默认初始化,局部变量没这功能,所以必须自己初始化。  
还要注意静态成员变量也没系统默认初始化  

### class文件用中文吗   

class文件可以用中文，但是不符合规范

### 数据类型   

基本数据类型：  

数据类型|字节数  
----------|-------
byte  Boolean|1个字节  
short char   |2个字节  
int   float  |4个字节  
long  double |8个字节  

### 访问修饰符
private：在同一类中可见，修饰变量和方法，不能修饰类
default(空缺，什么都不写)：在同一个包内可见，类，接口，变量和方法
protected：对同一包内的所有子类可见，变量和方法，不能修饰类
public：对所有类：类，接口，变量，方法  

### &和&&的区别  

1、具有按位与和逻辑与两个功能  
2、&&作为逻辑与具有短路的特点，当前面的条件表达式为false时就不会进行后面条件表达式的判断，可以用来避免空指针异常

### this关键字  

1、this调用当前属性  
2、this调用方法(普通方法和构造方法)  
* 静态方法不可以调用this方法，因为没有实例化  

### final 
1、final，finally，finallize的区别

final可以修饰列，变量，方法，修饰类表示该类不能被继承、修饰方法表示该方法不能被重写、修饰变量表示变量不能被重新赋值  
finally一般作用在try-catch代码块中，在处理异常的时候，通常我们将一定要执行的代码方法finally代码块中，表示不管是否有异常，该代码块都会被执行，一般用来存放一些关闭资源的代码  
finalize是一个方法，属于object的一个方法，该方法一般有垃圾回收器来调用，当我们调用System.gc()方法的时候，由垃圾回收器调用finalize(),回收垃圾，一个对象是否可回收判断  

## 循环结构  

1、do-while:循环至少执行一次循环体,满足条件执行，不满足停止执行   

2、for循环：两个for循环，当里面for循环写了break，外面循环继续  

## 集合框架  

1、集合有哪些类和接口，各自有什么特点  
两个接口：collection和map  
Collection包括List，Set，Queue(队列) ，
map：key-value键值对形式的集合，主要包括Hashmap，LinkedHashMap和treeMAp

2、collection和Collections有什么区别   
a、Collection是一个集合的接口，它包括list有序集合、set无序集合、queue队列等   
b、Collections则是Collection的工具类，为Collection类型的对象提供了很多方法

3、List接口和Set接口的区别  
List：是一个有序的集合，存储和取出元素顺序相同，允许存储重复的元素，有索引，可以使用普遍的for循环
Set：无序，不可重复的集合，没有索引，不能使用普遍的for循环，LinkedHashSet集合是一个有序的集合  
Map:key-value键值对形式的集合，添加或获取元素时，需要用key来检索value  


4、ArrayList和Linkedlist的区别  
1、ArrayList是实现基于动态数组的数据结构，LinkedList基于链表的数据结构(LinkedList是双向链表)  
2、对于随机访问get和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针。  
3、对于新增和删除操作add和remove，LinkedList比较占优势，因为ArrayList要移动数据   

5、hashmap  
1、底层原理  
基于hashing的原理，jdk8后采用数组+链表+红黑树的数据结构。允许空键和空值，我们通过put和get存储和获取对象。当我们给put()方法传递键和值时，先对键做一个hashCode()的计算来得到它在bucket数组中的位置来存储Entry对象。当获取对象时，通过get获取到bucket的位置，再通过键对象的equals()方法找到正确的键值对，然后在返回值对象。

6、hashmap怎么进行扩容  
利用resize()方法进行扩容，扩容过程是需要把旧表每个键进行重哈希然后写入扩容后的新表中，每次扩大两倍

7、hashcode和equals方法的联系  
java规定如果两个对象的hashcode()相同，那么他们的equals()不一定相同，equals相同，hashcode()一定相同  

8、hashmap，hashtable，hashset的区别  
* hashtable和hashmap
1.Hashtable是同步的，可以在一个多线程的应用中不采取任何特殊措施使用Hashtable；HashMap是非synchronized的，但collection框架提供方法能保证HashMap synchronized；  
2.HashMap允许键和值为null。HashMap可以让你将空值作为一个表的条目的key或value。HashMap中只有一条记录可以是一个空的key，但任意数量的条目可以是空的value。  
  
* HashMap和HashSet的区别
1.HashSet实现了Set接口，它不允许集合中有重复的值，当我们将对象存储在HashSet之前，要先确保对象重写equals()和hashCode()方法；这样才能比较对象的值是否相等，以确保set中没有储存相等的对象。如果我们没有重写这两个方法，将会使用这个方法的默认实现
2.HashMap实现了Map接口；HashSet仅仅存储对象，HashMap储存键值对
3.HashSet使用add()方法将元素放入set中，HashMap使用put()方法将元素放入map中
4.HashMap中使用键对象来计算hashcode值；HashSet使用成员对象来计算hashcode值，对于两个对象来说hashcode可能相同，所以equals()方法用来判断对象的相等性，如果两个对象不同的话，那么返回false
5.HashMap比较快，因为它使用唯一的键来获取对象；HashSet较HashMap来说比较慢

## 面向对象

### 接口和抽象类的区别

接口抽象异同：  
1、都能包含抽象的方法，这些抽象方法用于描述具备的功能，不提供具体的实现  
2、接口收对事物行为的抽象，而抽象类是对事物本质的抽象
3、接口中的变量要给初始值，抽象类可以不给
4、一个类只能继承一个抽象，但可以实现多个接口
5、抽象类中可以写非抽象类的方法，从而避免子类中重复书写，接口中只能有抽象方法  


### 重载和重写的区别：  

重写是子类存在方法与父类的方法的名字相同，而且参数的个数与类型一样，返回值也一样，
(子类与父类多态）
重载是一个类中定义了多个方法名相同，而他们的参数的数量不同或数量相同而类型和次序不同为重载
（一个类多态）

### ==和equals的区别  

==：1、对于基本数据类型，他们是作为常量在方法区中的常量值里面以hashset策略存储起来的，在常量池中，一个常量只会对应一个地址，因此基本数据类型和String常量是可以直接通过==来直接比较的。  
   2、==是直接比较的两个对象的堆内存地址，如果相等，则说明这两个引用实际是指向同一个对象地址的  

equals： equals方法是可以由我们自己重写的，不一定只是比较对象的内容   

## String类

1、String类能不能被继承？为什么?  

不能，因为String类是被final修饰的类，final修饰过的类不能被继承，final修饰过的变量不能被修改

2、String和StringBuilder，StringBuffer的区别

Java平台提供了两种类型的字符串：String和StringBuffer/StringBuilder，他们可以存储和操作字符串
String是只读字符串，也就意味着String引用的字符串内容是不能改变的。
但是StringBuilder/StringBuffer类表示的字符串对象可以进行直接修改，
Stringbuilder是单线程环境下使用的。因为它的所有方面都没有被synchronized修饰，效率也会比Stringbuffer高

## 多线程  

创建多线程：实现Runnable接口，重写run方法，或者继承Java.lang.Thread类，重写run方法

1、多线程的五种状态也是线程的生命周期：新建状态、就绪状态、运行状态、阻塞状态及死亡状态。  

2、一个进程的生命周期：1、进程创建  2、进程启动  3、进程状态切换  4、进程终止  

3、死锁的状态是怎么造成的  

两个或两个以上的进程在执行过程中，由于竞争资源或者由于彼此通信而造成的一种阻塞的现状，没有外力作用他们都无法推进下去。  
通俗来说就是两个线程同时占用两个资源，但又在彼此等待对方释放锁  

4、java是怎么实现线程安全的？
锁机制，用synchronize，lock给共享资源上锁
使用Java提供的安全类，java.util.concurrent包下的类自身就是线程安全的，在保证安全的同时保证性能

5、Sleep和wait的区别   
1、sleep是Thread方法，wait是object方法  
2、sleep方法没有释放锁，wait方法有释放锁  
3、wait，notify。notifyAll只能在同步控制方法和同步控制块里面使用，sleep任何地方   
4、sleep必须捕获异常，wait不用  

6、start和run方法的区别  
1、start方法用于启动线程，真正实现了多线程，调用了start方法后，会在后台创建一个新的线程来执行，不需要等待run方法执行完毕就可以继续执行其他代码，调用start方法时，该线程处于就绪状态，并没有要执行   
2、run方法也叫做线程体，包含了要执行的线程的逻辑代码，在调用run方法并没有创建新的线程，而是直接运行run方法中的代码。

7、阻塞产生的原因  
该线程放弃 CPU的使用，暂停运行，只有等到导致阻塞的原因消除之后才回复运行。或者是被其他的线程中断，该线程也会退出阻塞状态，同时抛出InterruptedException  

8、阐述java中的io，nio，bio  
i/o即input/output，就是指读写操作  
如果把io和nio放在一起比较的话，那这里的io可以理解为bio，即blocking-io  

bio(同步阻塞)：bio是Java传统的io模型，他是同步阻塞io，一个线程触发io操作后，必须等待这个io操作执行完成，期间不能去做其他事  
nio(同步非阻塞)：nio是同步非阻塞io，一个线程触发io操作后它可以立即返回，但是他需要不断的轮询去获取返回结果  
aio(异步非阻塞)：一个线程触发io操作后她可以立马返回去做其他事情，内核系统将io操作执行完毕成后会通知线程  
多路复用io(异步阻塞io)，一个线程可以管理多个连接，不用来回切换

## 异常   

1、有哪些异常的处理方法  
1、抛出异常，throws作用在方法上，throw作用在方法内  
2、try-catch进行异常的捕获

## IO流  
 

## 排序问题  

1、时间复杂度：冒泡排序，选择排序，插入排序，归并排序，堆排序，快速排序  
2、稳定：冒泡排序，归并排序  
3、不稳定：快速排序，堆排序  

