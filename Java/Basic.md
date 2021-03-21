# Java  

## 标识符   

1、什么是标识符？  
   * 在Java源程序当中凡程序员有权利自己命名的单词都是标志符  
   * 标志符在Editplus编辑器当中以黑色字体高亮显示  
   * 标志符可以标识什么元素呢？  
   类名，变量名，方法名，常量名  

2、标识符的命名规则？<不按照这个规则来，编译器会报错，这是语法>  
    * 只能由“数字、字母、下划线_、美元符号￥组成，不能含有其他符号  
    * 不能数字开头  
    * 严格区分大小写  
    * 关键字不能做标识符  
    * 理论上无限度限制，但是最好不要太长  

3、标识符的命名规范？  
* 最好的见名如意  
* 遵守驼峰规则  
  SystemService  
  UserService  
  CustomerService  
* 类名、接口：首字母大写，后面每个单词首字母大写  
* 变量名、方法名：首字母小写，后面每个单词首字母大写  
* 常量名：全部大写  

## 数据类型  

1、当数据类型不一样时，将会发生数据类型的转换。  
自动类型转换（隐式）  
* 特点：代码不需要进行特殊处理，自动完成。  
* 规则：数据范围从小到大。  

强制转换类型转换（显示）  
* 特点：代码需要进行特殊的格式处理，不能自动完成。  
* 格式：范围小的类型  范围小的变量名 = （范围小的类型）原本大的数据
注意事项  
1、强制类型转换一般不推荐使用，因为可能发生精度损失、数据溢出  
2、Byte/short/char，这三种类型都可以发生数学运算，例如加法“+”  
3、Byte/short/char这三种类型在运算的时候，都会被首先提升成为int类型，然后再计算  

```java
char zifu1='A';
System.out.println(zifu1+1);
//char类型进行数学运算，字符会按照ASCII码翻译
//输出66
```

```java
Byte num1=40;
byte num2=50;
//byte+byte-->int+int-->int
int result1=num1+num2;
//byte result=num1+num2
```

4、对于byte/char/short三种数据类型来说，如果右侧赋值的数值没有超过范围。那么javac编译器将会自动隐含的将为我们补上一个（byte）(short)(char)  

```java  
public class Demo12notice{
    public static void main(String[] args){
        //右侧确实是一个int数字，但是没有超过左侧的范围，就是正确的。
        //int-->byte,不是自动转换类型
        byte num1=/*（byte）*/30；//右侧没有超过左侧的范围
        System.out.println(num1);//30

    }
}
```

## 方法  

定义一个方法的格式：  
public static void 方法名称(){  
    方法体  
    }  
方法的名称的命名的规则和变量是一样的，使用小驼峰  
方法体：也就是大括号当中可以包含任意条语句  

注意事项：  
1、方法定义的先后顺序无所谓。  
2、方法的定义不能产生嵌套包含关系。  
3、方法定义好了之后，不会执行的。如果要想执行，一定要进行方法的【调用】  
如何调用方法，格式：  
方法名称（）；  


```java
public class Demo11Method{
    public static void main(String[] args){
        famer();//调用农名
        seller();//调用小商贩
        cook();//调用厨子的方法
        me();//调用我自己方法
    }
    public static void cook(){
        System.out.println("洗菜“)；
        System.out.println("切菜”)；
        System.out.println("炒菜“)；
        System.out.println("装盘");
    }
}
```


## if语法  

if语句第一语句格式：  

if(关系表达式){  
    语句体；  
    }  

```java
public class Demo02If{
    public static void main(String[] args){
        System.out.println("今天天气不错，正在压马路、、突然发现网吧”)；
        int age=16；
        if (ages>=18){
            System.out.println(进入网吧开始嗨！)
        }
        System.out.println("回家吃饭")
    }
}
```

if语句第2种语句格式：  
if（关系表达式）{  
    语句体1；  
    }else{  
        语句体2；
    }  

```java
public static void main(String[] args){
    //判断给定义的数据是奇数还是偶数
    //定义变量
    int a=1；
    if(a%2==0){
        System.out.println("a是偶数”)；
    }else{
        System.out.println("a是奇数");
    }
    System.out.println("结束");
}
```

if语句第三种语句格式：  
if（判断条件1）{  
    执行语句1；  
    }else if（判断语句2）{  
    执行语句2；  
    }eles{  
        执行语句n+1；
    }  

```java
public static void main(String[] args){
    int x=5；
    int y；
    if(x>=3){
        y=2*x+1;
    } else if (x>=-1&&x<3){
        y=2*x;
    }else{
        y=2*x-1;
    }
    System.out.println("y的值是："+y);
}
```

