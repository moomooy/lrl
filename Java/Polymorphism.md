# 多态

## 什么是多态  

多态，简而言之就是同一个行为具有多个不同表现形式或形态的能力。

## 多态的优点  

1、提高了程序的扩展性  
2、降低了代码之间的耦合  

## 多态的条件

1、继承。在多态中必须存在有继承关系的子类和父类。  
2、重写。子类对父类的默些方法重新定义，在调用这些方法的时候就会调用子类的方法。  
3、向上转型。在多态中需要将子类的引用赋值给父类对象，只有这样该引用才能具备技能调用父类的方法和子类的方法。  

```java
public class Animal {
    public void eat() {
        System.out.println("animal eatting...");
    }
}
```

```java
public class Cat extends Animal {

    public void eat() {

        System.out.println("Cat eat fish");
    }
}
```

```java
public class Dog extends Animal {

    public void eat() {
        System.out.println("Dogs eat bones");
    }

    public void run() {
        System.out.println("I can run");
    }
}
```

```java
public class unline {

    public static void main(String[] args) {
        Animal animal = new Dog();//向上转型
        animal.eat();
    }

}
```
这就是向上转型，Animal animal = new Dog();  
将子类对象Dog转化为父类对象Animal。这个时候animal这个引用调用的方法是子类方法。

## 多态成员访问特点

成员变量 编译看左边(父类),运行看左边(父类)  
成员方法 编译看左边(父类)，运行看右边(子类)。动态绑定  
静态方法  编译看左边(父类)，运行看左边(父类)。  
静态和类相关，算不上重写，所以，访问还是左边的，只有非静态的成员方法,编译看左边,运行看右边