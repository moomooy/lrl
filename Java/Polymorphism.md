# 多态

## 什么是多态  

多态，简而言之就是同一个行为具有多个不同表现形式或形态的能力。不同形态是指编译时多态，运行时多态

### 编译时多态（静态多态性）

编译时多态，也可以叫做静态多态性，静态绑定。方法带final、static、private时是编译时多态，因为可以直接确定调用哪个方法。
1.方法重载：
方法重载就是在同一个类中，出现了多个同名的方法，他们的参数列表(方法签名)不同 (参数列表的个数不同，参数列表的数据类型不同，参数列表的顺序不同)。根据实际参数的数据类型、个数和次序，Java在编译时能够确定执行重载方法中的哪一个。  
2.方法重写时的编译时多态：  
除了重载，重写也表现出两种多态性。当一个对象的引用指向的是当前对象所属类的对象时，为编译时多态。

```java
public class Static {
    int add(int a, int b) {
        return a + b;
    }

    int add(int a, int b, int c) {
        return a + b + c;
    }
}
```

```java
public class Dome {
    public static void main(String args[]) {
        Static obj = new Static();
        System.out.println(obj.add(10, 20));
        System.out.println(obj.add(10, 20, 30));
    }
}
```

### 运行时多态（动态多态性）

运行时多态，也叫作动态绑定，一般是指在执行期间（非编译期间）判断引用对象的实际类型，根据实际类型判断并调用相应的属性和方法。主要用于继承父类和实现接口时，父类引用指向子类对象。  
对于多态时的成员函数，总的来说分为三种情况：  
1、父类有方法，子类有覆盖方法：编译通过，执行子类方法。  
2、父类有方法，子类没覆盖方法：编译通过，执行父类方法（子类继承）。  
3、父类没方法，子类有方法：编译失败，无法执行。

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

## 多态的优点  

1、提高了程序的扩展性  2、为什么
2、降低了代码之间的耦合  3为什么

## 多态的条件（运行时）还要写出编译时的

1、继承。在多态中必须存在有继承关系的子类和父类。  
2、重写。子类对父类的默些方法重新定义，在调用这些方法的时候就会调用子类的方法。  
3、向上转型。在多态中需要将子类的引用赋值给父类对象，只有这样该引用才能具备技能调用父类的方法和子类的方法。  

这就是向上转型，Animal animal = new Dog();  
将子类对象Dog转化为父类对象Animal。这个时候animal这个引用调用的方法是子类方法。

## 多态成员访问特点

成员变量 编译看左边(父类),运行左看边(父类)  
成员方法 编译看左边(父类)，运行看右边(子类)。动态绑定  
静态方法  编译看左边(父类)，运行看左边(父类)。  
静态和类相关，算不上重写，所以，访问还是左边的，只有非静态的成员方法,编译看左边,运行看右边