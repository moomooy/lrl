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

## Linux  

1.怎么运用Linux查询多线程在哪个cpu上面运行  
   ps -eo ruser,pid,ppid,lwp,psr,args -L | grep qemu  
   依次在用户ID，进程ID，父进程ID，线程ID，运行该线程的CPU的序号，命令行参数（包括命令本身）  

2.怎么运用Linux查询多线程  
   ps -ef | grep  
   ps -ef:显示所有进程的消息  
   grep是查找输出包含想要的字符串的行


## Java  

### 面向对象  

1、这个题目考察的是向上转型，用的是强制转型的格式：  
父类名称 对象名 = (父类名称) 子类对象；Base baseObj = (Base)anObj;    
一般是采用多态的写法：父类名称 对象名 = new 子类名称(); Base baseObj = new Child();   


```java
public class Test01 {
    public static void main(String[] args) {
      Child anObj =new Child();
      Base baseObj = (Base)anObj;
      baseObj.text();

    }
}

public class Base {
    void text(){
        System.out.println("Base.test()");
    }
}

public class Child extends Base{
    void test(){
        System.out.println("child.text");
    }

}
```

### 静态static  

定义、一旦使用static修饰成员方法，那么这就成为了静态方法。静态方法不属于对象，而是属于类的   

1、静态方法能访问该类的静态方法成员变量  
2、静态变量并不是说其就不能改变值的，静态值是可变的。   
3、静态方法属于类，所以可被类中所有的方法访问  
4、该类的对象也可以共享静态里面的成员变量的值   

### final关键字  

final修饰方法后，该方法不允许被重写，继承和重载  
但final修饰的变量不用立即赋值，在对象创建之前完成赋值的过程就可以。  

### 接口  

1、接口中的方法都是默认public 和 abstract 的。所以在实现接口的类中，实现方法时都要在方法前加上 public 修饰符。  
2、实现抽象类和接口的类必须实现其中的方法，除非也是抽象类  
3、接口中定义的变量都是public static final型，且必须给其赋初值，  
4、抽象类中可以没有抽象方法，抽象类可以包含抽象方法、非抽象方法和抽象访问器。可以创建一个变量，其类型是一个抽象类，并让它指向具体子类的一个实例。不能有抽象构造函数或抽象静态方法。

### 进程和线程  

1、下列关于进程的叙述，正确的是（C）  
A.系统级线程和用户级线程的切换都需要内核的支持  
* 用户级线程切换不需要通过内核，因为用户级线程只在用户进程的空间内活动，系统并不能感知到用户级线程的存在，所以用户级线程的切换不需要通过内核。系统级线程的切换是需要内核支持的

B.同一进程中的各个线程拥有各自不同的地址空间   
* 同一进程下的各线程共享进程的地址空间，并共享进程所持有的资源，但线程有自己的栈空间，不与其他线程共享  

C.不管系统是否支持线程，进程都是资源分配的基本单位。  
* 进程始终是操作系统资源分配的基本单位，线程不能直接被系统分配资源。  

D.线程是资源分配的基本单位，进程是调度的基本单位  
* 进程始终是操作系统资源分配的基本单位,线程可以参与调度，如系统级线程可以被系统直接调度执行


## 数据结构   

1、深度为5的满二叉树，叶子结点的个数是———16  
解释：在一棵满二叉树中，节点的个数为2^n-1，叶子节点的个数为：2^(n-1)。  



