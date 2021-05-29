# 面试经历的问题  
  
## MySQL  

1.当一张表上有学号成绩,另一张表上有学号姓名,怎么样连接两张表查询出不及格的同学  

首先了解主键和外键  :  
主键(primary key):主键是唯一的，用于标识一张表。
外键(foreign key):存在与外面的主键就是外键,外键可以有多个，用于建立表和表的关系。    


连接语句:  
LEFT JOIN（左连接）：返回包括左表中的所有记录和右表中连接字段相等的记录   

左连接语句:SELECT tb_student.name,tb_class.name FROM tb_student LEFT OUTER JOIN tb_class ON tb_student.classID=tb_class.id;  

RIGHT JOIN（右连接）：返回包括右表中所有记录和左表中连接字段相等的记录  

查询语句:SELECT * FROM tb_score WHERE grade> ANY(SELECT grade FROM tb_score WHERE sID=1);  

2、关于事务的了解  
访问并可能操作各种数据项的一个数据库操作序列，这些操作要么全部执行,要么全部不执行，是一个不可分割的工作单位。事务由事务开始与事务结束之间执行的全部数据库操作组成。


## Linux  

1.怎么运用Linux查询多线程在哪个cpu上面运行  
   ps -eo ruser,pid,ppid,lwp,psr,args -L | grep qemu  
   依次在用户ID，进程ID，父进程ID，线程ID，运行该线程的CPU的序号，命令行参数（包括命令本身）  

2.怎么运用Linux查询多线程  
   ps -ef | grep  
   ps -ef:显示所有进程的消息  
   grep是查找输出包含想要的字符串的行


## Java  


### 集合框架  

1、ArrayList和Linkedlist的区别  

1、ArrayList是实现基于动态数组的数据结构，LinkedList基于链表的数据结构(LinkedList是双向链表)  
2、对于随机访问get和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针。  
3、对于新增和删除操作add和remove，LinkedList比较占优势，因为ArrayList要移动数据   

## 重写和重载  

1、重载和重写的区别：  

重载：是定义相同的方法名，参数不同  
重写：子类重写父类的方法
重载是在一个类中，重写是子类与父类之间；  
重载是编译时的多态性，重写时运行时的多态性。  

## 数据类型：  

基本数据类型：  

数据类型|字节数  
----------|-------
byte  Boolean|1个字节  
short char   |2个字节  
int   float  |4个字节  
long  double |8个字节  


## ==和equals的区别  

==：1、对于基本数据类型，他们是作为常量在方法区中的常量值里面以hashset策略存储起来的，在常量池中，一个常量只会对应一个地址，因此基本数据类型和String常量是可以直接通过==来直接比较的。  
   2、==是直接比较的两个对象的堆内存地址，如果相等，则说明这两个引用实际是指向同一个对象地址的  

equals： equals方法是可以由我们自己重写的，不一定只是比较对象的内容   

## 抽象类和接口的区别  

a、抽象类不能被实例化只能被继承；  
b、包含抽象方法的一定是抽象类，但是抽象类不一定含有抽象方法；  
c、抽象类中的抽象方法的修饰符只能为public或者protected，默认为public；  
d、一个子类继承一个抽象类，则子类必须实现父类抽象方法，否则子类也必须定义为抽象类；  
e、抽象类可以包含属性、方法、构造方法，但是构造方法不能用于实例化，主要用途是被子类调用。

接口：Java中接口使用interface关键字修饰，特点为:
a、接口可以包含变量、方法；变量被隐士指定为public static final，方法被隐士指定为public abstract（JDK1.8之前）；
b、接口支持多继承，即一个接口可以extends多个接口，间接的解决了Java中类的单继承问题；
c、一个类可以实现多个接口；
 

## 多线程的状态  

新建状态、就绪状态、运行状态、阻塞状态及死亡状态。  

## currenthasmap  

后续学hashtable了解  

## this关键字  

1、this调用当前属性  
2、this调用方法(普通方法和构造方法)  
* 静态方法不可以调用this方法，因为没有实例化  

## 反射  

