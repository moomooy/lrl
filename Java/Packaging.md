# 封装

1、什么是封装？  
封装是指隐藏对象的属性和实现细节，仅对外提供公共访问方式。  
2、封装的优点：  
隐藏代码的实现细节，提高安全性。

```java
public class Person {
    private String name;
    private int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        if (age <= 0) {
            System.out.println("you entered the age incorrectly");
        } else {
            this.age = age;
        }
    }

    public void speak() {
        System.out.println("I am" + name + ",I am" + age + "years old");
    }
}
```

```java
public class Example01 {
    public static void main(String[] args) {
        Person p = new Person();
        p.setName("lily");
        p.setAge(10);
        p.speak();
    }
}
```
