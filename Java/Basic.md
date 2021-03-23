# java编程基础

## Java的基本语法  

### 标识符

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

### 定义

定义：方法是就是若干个语句的功能的集合。  

定义一个方法完整的格式：  

public static（修饰符） void（返回值类型） 方法名称(参数类型 参数名称，...){  
    方法体  
    return  返回值；  
    }  

### 名词解释  

修饰符：现阶段的固定写法，public static  
返回值类型：也就是方法最终产生的数据结果是什么类型  
方法名称：方法的名字，规则和变量一样，小驼峰  
参数类型：进入方法的数据是什么类型  
参数名称：进入方法的数据对应的变量名称  
ps：参数如果有多个，使用逗号进行分隔  
方法体：方法需要做的事情。若干个代码  
return：两个作用，第一停止当前方法，第二将后面的返回值还给调用处  
返回值：也就是方法执行后最终产生的数据结果
ps：return后面的“返回值”，必须和方法前面的“返回值类型",保持对应

### 注意事项：  

1、方法定义的先后顺序无所谓。  
2、方法的定义不能产生嵌套包含关系。  
3、方法定义好了之后，不会执行的。如果要想执行，一定要进行方法的【调用】  
4、此前学习的方法，返回值类型固定写为void，这种方法只能够单独调用，不能进行打印

### 方法的三种调用格式  

1、单独调用：方法名称（参数）；  
2、打印调用：System.out.println(方法名称（参数）)；  
3、赋值调用：数据类型  变量名称=方法名称（参数））；

### 例子  

定义一个两个int的的数字相加的方法。三要素：  
返回值类型：int  
方法名称：sum  
参数列表：int a，int b  


```java
public class Demo11Method{
    public static void main(String[] args){
        //单独调用
        sum(10,20);
        System.out.println("===========");

        //打印调用
        System.out.println(sum(10,20));//30
        System.out.println("============");

        //赋值调用
        int number=sum(15,25);
        number+=100;
        System.out.println("变量的值"+number);
    }
    public static int sum(int a,int b){
        System.out.println("方法执行了")；
        int result=a+b;
        return result;
    }
}
```

## 选择结构语句  

### if语法  

#### if语句第一语句格式：  

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

#### if语句第2种语句格式：  
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

#### if语句第三种语句格式：  
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

### switch语句  

switch语句格式：  

```java
switch (表达式){
    case 常量值1;
    语句体1；
    break；
    case 常量值2;
    语句体2；
    break；
    ...
    default;
    语句体n+1；
    break；
}
```

例子：  

```java
public static void main(String[] args){
    int num1=1;
    switch(num){
        case 1;
        System.out.rintln("星期一")
        break;
        case 2;
        System.out.println("星期二")
        break;
        case 3;
        System.out.println("星期三")
        break;
        case 4;
        System.out.println("星期四")
        break;
        case 5;
        System.out.println("星期五")
        break;
        case 6;
        System.out.println("星期六")
        break;
        case 7;
        System.out.println("星期七")
        break;
        default；
        System.out.println("数据不合理")
        break;
            }
}
```

注意事项：  
1、多个case后面的数据不可以重复。  
2、switch后面小括号当中只能下列数据类型：  
   基本数据类型：byte/short/char/int  
   引用数据类型String字符串、emu枚举  
3、switch语句格式可以很灵活：前后顺序可以颠倒，而且break语句还可以省略。  
"匹配哪一些case就从哪一个位置向下执行，直到遇到了break或者整体结束为止。"  

## 循环结构语句  

### 循环语句for  

语句格式：  
for（初始化表达式;布尔表达式;步进表达式）{  
    循环体；  
    }  

```java
public class Demo09FOr{
    public static void main(String[] args){
        for(int i=1;i<=100;i++){
            System.out.println("我错了");
        }
    }
}
```

### 循环语句while  

while有一个标准格式，还有一个扩展格式。  

标准格式：  
while（条件判断）{  
    循环体  
    }  

扩展格式：  
初始化语句；  
while（条件语句）{  
    循环体；  
    }  

```java
public class Demo10while{
    public static void main(String[] args){
        int i=1;
        while(i<10){
            System.out.println("我错了"+i);
            i++;
        }
    }
}
```

### do-while循环语句  

扩展格式：  

初始化语句  
do{  
    循环体  
    步进语句  
    }while(条件判断)；  

```java
public class Dome11Dowhile{
    public static void main(String[] args){
        int i=1;
        do{
            System.out.println("aaa"+i);
        }while(i<=10);
    }
}
```

### 三种循环的区别  

1、如果条件判断从来没有满足过，那么for循环和whil循环将会被执行0次，do-while至少执行1次。  

2、for循环的变量在小括号中定义，只有循环内部才可以被使用，其他两个初始化语句在外面，所以除了循环还可以继续使用。  

### break语句  

break关键字的用法有常见的两种：  

1、可以放在switch语句当中，一旦执行，整个switch语句立刻结束；  
2、还可以放在循环语句当中，一旦执行，整个循环语句立刻结束，打断循环。  

循环的一个建议：  
凡是次数确定的场景，多用for循环，否则多用while循环。  

```java
public class Dome14Break{
    public static void main(String[] args){
        for(int=1;i<=10;i++){
            //如果希望从第四次开始，后续全部不要了，就打断循环
            if(i==4){
                break;//那么打断整个循环
            }
            System.out.println("hello"+i);
            //输出到hello3后面就没有了
        }
    }
}
```

### continue语句  

另一种循环控制语句是continue关键字。  
一旦执行，立刻跳过当前次循环，马上开始下一次循环。  

```java
public class Demo15continue{
    public static void main(String[] args){
        for(int i=1;i<=10;i++){
            if(i==4){
                continue;//跳过第四层的循环，马上开始第五层
            }
            System.out.println(i+"层到了");
        }
    }
}
```

### 死循环  

永远停不下来的循环叫做死循环。  

死循环的标准格式：  
while（true）{
    循环体
    }  

```java
public class Demo16Deadloop{
    public static void main(String[] args){
        while(true){
            System.out.println("aaaa");
        }
    }
}
```

### 嵌套循环  

例子：  

```java
public class Demo{
    public static void main(String[] args){
        for(int hour=0;hour<24;hour++){
            for(int m=0;m<60;m++){
                System.out.println(hour+"点"+m+"分");
            }
        }
    }
}
```

