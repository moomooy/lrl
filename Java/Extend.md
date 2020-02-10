# java

## 类  

在Java语言里，最基本的单位是类（class），类=成员变量+方法  
类是一组相关属性和行为的集合，类一般泛指莫一件事定义类的。  
成员变量：在类的内部，方法的外部定义的变量叫做成员变量  
局部变量：在方法内部定义的变量叫做局部变量

## 方法

第一步，访问修饰符  
第二步，关键词。关键词主要有static和abstract两个关键词  
第三步，返回值有否？如果有返回值就是有返回值方法。有返回值，则写具体返回类型，比如string int 等，这就是java强类型的一个表现。第四步。方法的名称。为了见名知意，也就是可以自定义。第五步，参数列表。现实是多姿多彩的，需要很多的形容词来修饰，而在编程中就需要很多的变量来修饰 第六步。方法体。主要的区别就在于有无。也就是有具体的方法体以及没有方法体。甚至都可以没有大括号。小括号就能组成一个方法。 最简单的方法就是方法名（）

## 对象

对象有三个特征：继承，封装，多态.

### 继承

实现：Extends 原理：子类可以继承父类的所有属性和方法
例如这题  

``` java
 public class Cleanser {
    private String s = new String("Cleanser");

    public void append(String a)
    {
        s += a;
    }

    public void dilute()
    {
        append("dilute()");
    }
        public void apply ()
        {
            append("apply()");
        }
        public void scrub ()
        {
            append("scrub()");
        }
        public void print ()
        {
            System.out.println(s);
        }
        public static void main (String[] args)
        {
            Cleanser x = new Cleanser();
            x.dilute();
            x.apply();
            x.scrub();
            x.print();
        }
    }
```  

```java
public class Detergent extends Cleanser {
    // Change a method:
    public void scrub()
    {
        append(" Detergent. scrub()");
        super.scrub(); // Call base-class version
    }
        // Add methods to the interface:
        public void foam ()
        {
            append(" foam()");
        }
        // Test the new class:
        public static void main (String[] args)
        {
            Detergent x = new Detergent();
            x.dilute();
            x.apply();
            x.scrub();
            x.foam();
            x.print();
            System.out.println("Testing base class:");
            Cleanser.main(args);
        }
    } ///:
```

在这题中Detergent是洗涤剂  
cleanser是清洁剂洗脸的  
gvcappend是增加，附加  
 dilute是稀释冲淡  
 apply是涂  
 scrub是擦  
 foam是泡沫  
 子类继承了父类的x.dilute();x.apply();x.scrub();x.print();这些方法，比较公用的方法一般放在父类里d
