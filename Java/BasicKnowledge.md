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

永远停不下来的叫做死循环的的。  

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


## 数组  

数组的概念：是一种容器，可以同时存放多个数据只值。  

数组的特点：  
1、数组是一种引用数据类型  
2、数组当中的多个数据，类型必须统一  
3、数组的长度在程序运营期间不可改变  

数组的初始化：在内存中创建一个数组，并且像其中赋予一些默认值  

### 两种常见的初始化方式：  

1、动态初始化（指定长度）  
2、静态初始化（指定内容）  

动态初始化数组的格式：  
数组类型[] 数组名称 = new 数据类型[数组长度];

左侧数据类型：也就是数组当中保存的数据，全部都是统一的什么类型  
左侧的中括号：代表我是一个数组  
左侧数组名称，给数组取个名字  
左侧的new，代表创建的动作  
左侧数据类型，必须和左边的数据类型保持一致  
右侧的中括号长度，也就是数组当中，到底可以保存多少个数据，是一个int数字  

```java
public class Demo01Array{
    public static void main(String[] args){
        //创建一个数组，里面可以存放300个int数据
        //格式：数据类型[] 数组名称 = new 数据类型[数组长度]
        int[]  arrayA = new int[300];

        //创建一个数组，能存放10个double类型的数据  
        double[] arrayB = new double[10]；

        //创建一个数组，能存放5个字符串 
        String[] arrayC = new String[5];
            }
}
```

静态初始化基本格式：   
数据类型[] 数组名称 = new 数据类型[] {元素1，元素2，...};   

静态省略格式：  
数据类型[] 数据名称 = {元素1，元素2，...};

```java
public class Demo02Array{
    public static void main(String[] args){
        //直接创建一个数组，里面装的全部是int数字，具体为5，15，25 
        int [] arrayA=new int[] {5,15,25};

        //创建一个数组，用来装字符串："hello","world","java" 
        String [] arrayB=new String []{"hello","world","java"}
    }
}
```

注意事项：  
1、静态初始化没有直接指定长度，但是仍然会自动推算得到长。  
2、静态初始化标准格式可以拆分成两个步骤。  
3、动态初始化也可以拆分成为两个步骤。  
4、静态初始化一旦使用省略格式，就不能拆分为两个步骤。  

使用建议：  
如果不确定数组当中的具体内容，用动态初始化；否则，已经确定了具体的内容，用静态初始化。  

```java
public class Demo03Array{
    public static void main(String[] args){
        //省略格式的静态初始化
        int[] arrayA = {10,20,30};

        //静态初始化的标准格式，可以拆分成为两个步骤
        int[] arrayB = {11,21,31};

        //动态初始化也可以拆分两个步骤  
        int[] arrayC;
        arrayC=new int[5];

        //静态初始化的省略格式，不能拆分成为两个步骤
        int[] arrayD;
        arrayD ={10,20,30};
            }
}
```

### 访问数组元素进行获取  

直接打印数组名称，得到的是数组的对应的，内存是地址哈希值。  

访问数组元素的格式：数组名称[索引值]  
索引值：就是一个int数字，代表数组当中元素的编号  
【注意】索引值从0开始，一直到“数组的长度-1”为止  

```java
public class Demo{
    public static void main(String[] args){
        //静态初始化的省略格式
        int[] array = {10,20,30};

        System.out.println(array);//[I@75412c2f

        System.out.println(array[0])；//10
        
        int num = array[1];
        System.out.println(num);//20
    }
}
```

### 访问数组元素进行赋值

如果动态初始化数组的时候，其中的元素将会自动拥有一个默认值，规则如下：  
如果是整点类型：那么默认值为0；  
如果是浮点类型，那么默认为0.0；  
如果是字符类型，那么默认为'\u0000'；
如果是布尔类型，那么默认为false；  
如果是引用类型，那么默认为null；  

注意事项：  
静态初始化其实也有默认值的过程，只不过系统马上将默认值替换成为了大括号当中的具体数值。  

```java
public class Demo05{
    public static void main(String[] args){
        //动态初始化一个数组
        int[] array = new int[3];

        System.out.println(array[0]);//0
          
        array[1]=123;
        System.out.println(array[0]);
    }
}
```
### 获取数组的长度  

如何获取数组的长度，格式：  
数组名称.length  
这将会得到一个int数字，代表数组的长度  

数组一旦创建，程序运营期间，长度不可以改变  

```java 
public class Demo{
    public static void main(String[] args){
        int[] arrayA=new int[3];
        int arrayB={1,2,3,4,5,6,7,8};
        int len=arrayB.length;
        System.out.println("arrayB数组的长度"+len);
        System.out..println("===============");

        int arrayC=new int[3];
        System.out.println(arrayC.length);
        arrayC=new int[5];
        System.out.println(arrayC.length);
    }
}
```

### 数组的遍历输出  

遍历数组：说的就是堆数组当中的每一个元素进行逐一，挨个处理，默认的处理方式就是打印输出。  

```java
public class Demo{
    public static void main(String[] args){
        //int len=array.length;//长度
        for (int i=0;i<array.length;i++){
            System.out.println(array[i]);
        }
    }
}
```

### 求数组中的最值

```java 
public class Demo{
    public static void main(String[] args){
        int[] array {5,15,30,20,10000};

        int max=array[0]；
        for(int i=1;i<array.length;i++){
            //如果当前元素，比max更大，则换人
            if(array[i]>max){
                max=array[i];
            }
        }
        System.out.println("最大值"+max)
    }
}
```

### 数组元素的反转  

本来的样子：[1，2，3，4]  
之后的样子：[4，3，2，1]  

要求是不能使用新的数组，就用原来那个数组。  

1、数组元素的交换，其实就是对称位置的交换  

2、通常遍历数组用的是一个索引；  
int i=0  
现在表示对称位置需要两个索引；
int min =0;int max=0;  

3、如何交换两个变量的值？  
找第三个变量到手  

4、什么时候应该交换？  
min<max  

```java
public class Demo{
    public static void main(String[] args){
        int[] array={1,2,3,4};

        /*初始化语句：int min=0;int max=array.length-1;
        条件判断：min<max
        步进表达值：min++;max--;
        循环体：第三个变量*/

        for(int min=0,max=arrayy.length-1;min<max;min++,max--){
            int temp=array[min];
            array[min]=array[max];
            array[max]=temp
        }
        for(int i=0;i<array.length;i++){
            System.out.println(array[i]);
        }
    }
}
```

### 数组作为方法的参数  

数组可以进行方法的参数。  

当调用方法的时候，向方法的小括号进行传参，传递进去的其实是数组的地址值  

```java 
public class Demo{
    public static void main(String[] args){
        int[] array={10,20,30,40,50};
        printArray(array);//传递进去的是array当中的地址值
        System.out.println("==============aaaaaa");
        printArray(array);
        System.out.println("==============bbbbaa");

    }

    public static void printArray(int[] array){
        for(int i=0;i<array.length;i++){
         System.out.println(array[i])
        }
            }
}
```

### 数组作为方法的返回值  

一个方法可以有0、1、多个参数，但是只能有0或者1个返回值，不能有多个返回值。  
如果希望一个方法当中产生了多个结果数据进行返回，则使用一个数组作为返回值类型即可  

任何数据类型都能作为方法的参数类型，或者返回值类型  

数组作为方法的参数，传递进去的其实是数组的地址值  
数组作为方法的返回值，返回的其实也是数组的地址值  

```java
public class Demo{
    public static void main(String[] args){
        int[] result = calculate(10,20,30);
        System.out.println("sum"+result[0]);
        System.out.println("avg"+result[1]);
    }
    public static int[] calculate(int a,int b,int c){
        int sum=a+b+c;
        int avg=sum/3;
        int[] array={sum,avg};
        return array;
    }
}
```
## 面向对象  

概述：  
面向过程：当需要实现一个功能的时候，每一个具体的步骤都要亲历亲为，详细处理每一个细节  
面向对象：当需要实现一个功能的时候，不关心具体的步骤，而是找一个已经具有该功能的人，来帮我做事  

```java
import java.until.Array;
public class Demo{
    public static void main(String[] args){
        //要求打印格式[10,20,30,40,50]
        //使用面向过程，每一个步骤细节都要亲历亲为  
        System.out.println("[");
        for(int i=0;i<array.length;i++){
            if(i==array.length-1){//如果时最后一个元素
            System.out.println(array[i]+"]");
            }else{//如果不是最后一个元素
            System.out.println(srray[i]+",");
            }
        }
        System.out.println("===============");

        //使用面向对象
        //找一个JDK给我们提供好的Array类，
        //其中有一个toString方法，直接就是把数组变成想要的格式的字符串
        System.out.println(Arrays.toString(array));
    }
}
```

### 类和对象  

#### 什么是类  

类：类是一组相关属性和行为的集合，可以看成是一类事物的模板，使用事物的属性特征和行为特征来描述事物  
现实中，描述一类事物：  
* 属性：就是该事物的状态信息  
* 行为：就是该事物能够做什么  
举例：小猫  
属性：名字，体重，年龄，颜色  
行为：走，跑，叫  

例子：定义一个类，用来模拟“学生”的事物，其中就有两个组成成分  

属性（是什么）：  
      姓名  
      年龄  
行为（能做什么）：  
      吃饭
      睡觉
      学习

对应到Java的类当中：  

成员变量（属性）；
     String name;//姓名  
     int age；//年龄  
成员方法（行为）；  
     public void eat(){}//吃饭  
     public void sleep(){}//睡觉  
     public void study(){}//学习  

注意事项：  
1、成员变量是直接定义在类当中的，在方法外边  
2、成员方法不要写static关键字  
     
```java
public class Student{
    //成员变量
    String name;//姓名
    int age;年龄

    //成员方法
    public void eat(){
        System.out.println("吃饭饭");
    }
    public void sleep(){
        System.out.println("睡觉觉");
    }
    public void study(){
        System.out.println("学习");
    }
} 
```

##### 定义一个标准的类

一个标准的类通常要拥有下面四个组成部分  

1、所有的成员变量都要使用private关键字修饰  
2、为每一个成员变量编写一对Getter/Setter方法  
3、编写一个无参数的构造方法  
4、编写一个全参数的构造方法  

这样标准的类也叫做java Bean

```java
public class Student{

    private String name;//姓名  
    private int age;//年龄

    public Student(){
    }

    public Student(String name,int age){
        this.name = name;
        this.age = age;X
    }

    public String getName(){
        return name;
    }

    public void setName(String name){
        this.name = name;
    }

    public int getAGe(){
        return age;
    }

    public void setAge(int age){
        this.age = age;
    }
}
```

 ### 什么是对象  

对象：是一类事物的具体表现，对象是类的一个实例，必然具备事物的属性和行为  
现实中：一类事物的实例：一只小猫（具备类的属性）  

通常情况下，一个类并不能直接使用，需要根据类创建一个对象，才能使用  

* 导包，也就是指出需要使用的类，在什么位置。  
import 包名称.类名称；
import cn.iscase.day06.demo01.Student;  
对于和当前类属于同一个包的情况，可以省略导包语句不写。  

* 创建，格式:  
类名称 对象名 = new 类名称（）；
student stu = new Student();  

* 使用，分为两种情况：  
使用类的成员变量： 对象名.成员变量名  
使用类的成员方法：对象名.成员方法名（参数）

```java
public class Demo{
    public static void main(String[] args){
        //导包。
        //我需要使用的Student类，和我自己Demo位于同一个包下，所以省略导包语句不写  

        //创建，格式：
        //类名称 对象名 = new 类名称();
        //根据Student类，创建了一个名为stu的对象
        Student stu = new Student();

        //使用其中的成员变量，格式：  
        //对象名.成员变量名
        System.out.println(stu.name);//null
        System.out,println(stu.age);//0

        //改变对象当中的成员变量数值内容
        //将右侧的字符串，赋值交给stu对象当中的name成员变量
        stu.name = "罗溶靓";
        stu.age = "18";
        System.out.println(stu.name);//罗溶靓
        System.out.println(stu.age)；//18

        //使用成员方法的格式
        //对象名.成员方法名
        stu.eat();
        stu.sleep();
    }
}
```

#### 匿名对象的说明 

一般创建对象的标准格式：  
类名称 对象名 = new 类名称();  

匿名对象就是只有右边的对象，没有左边的名字和赋值运算符。  
new 类名称();  
注意事项：匿名对象只能使用一次，下次再用不得不再创建一个新对象  
使用建议：如果确定有一个对象只需要使用唯一的一次，就可以使用匿名对象。  

类  
```java 
public class Demo{
    public static void main(String[] args){
        //左边one就是对象的名称  
        person one = new person();
        one.name = "高圆圆";
        one.showname();//我叫高圆圆
        System.out.println("===============");  

        //匿名对象
        new Person().name="john";
        new person().showname();//我叫null
    }
}
```

```java
public class Person{
    String name;

    public void showName(){
        System.out.println("我叫"+name);
    }
}
```

#### 匿名对象作为方法的返回参数和返回值  

```java
import java.util.Scanner;
public class Demo{
    public static void mian(String[] args){
        //普通使用费方式
        //Scanner sc = new Scanner(System.in);
        //int num = sc.nextInt();

        //匿名对象的方式
        //int num = new Scanner(System.in).nextInt();
        //System.out.println("输入的是"+num);

        //使用一般写法传入参数
        //Scanner sc = new Scanner(System.in);
        //methodParam(sc);

        //使用匿名对象来进行传参
        //methodParam(new Scanner(System.in));

        Scanner sc = methodReturn();
        int num = sc.nextInt();
        System.out.println("输入的是"+num);
    }
    public static void methodParam(Scanner sc){
        int num = sc.nextInt();
        System.out.println("输入的是"+num);
    }
    public static Scanner methodReturn(){
        //Scanner sc = new Scanner(System.in);
        //return sc;
        return new Scanner(System.in);
    }
}
```

### 类与对象的关系  

类是对一类事物的描述，是抽象的  
对象是一类事物的实例，是具体的   

* 类是对象的模板，对象是类的实体  
 举例：手机的设计图（抽象）真正的手机（具体）  

定义一个类，用来模拟“手机”事物。  
 属性：品牌、价格、颜色  
 行为：打电话、发短信  

对应到类当中：  
成员变量（属性）：  
String brand;//品牌  
double price；//价格  
String color；//颜色  
成员方法（行为）；  
public void call(String who){}//打电话  
public void sendMessage(){}//群发短信

```java
public class phone {
    //成员变量
    String brand;//品牌
    double price;//价格
    String color;//颜色

    //成员方法
    public void call(String who){
        System.out.println("给"+who+"打电话");
    }

    public void sendMessage(){
        System.out.println("群发短信");
    }
}
```

```java
package cn.itcase.day06.demo02;

public class demo{
    public static void main(String[] args){
        //根据phone类，创建一个名为one的对象
        //格式：类名称 对象名 = new 类名称（);
        one.brand="苹果";
        one.price=8388.0;
        one.color="黑色";
        System.out.println(one.brand);//黑色
        System.out.println(one.price);//8388.0
        System.out.println(one.color);//黑色

        one.call("乔布斯");//给乔布斯打电话
        one.sendMessage();//群发短息
            }
}
```

### 成员变量和局部变量的区别  

局部变量和成员变量  

1、定义的位置不一样【重点】  
局部变量：在方法的内部  
成员变量：在方法的外部，直接写在类当中  

2、作用范围不一样【重点】  
局部变量：只有方法当中才可以使用，出了方法就不能再用  
成员变量:整个类全部都可以通用  

3、默认值不一样【重点】  
局部变量：没有默认值，如果想要使用，必须手动赋值  
成员变量：如果没有赋值，会有默认值，规则和数组一样  

4、内存的位置不一样（了解）  
局部变量：位于栈内存  
成员变量：位于堆内存  

5、生命周期不一样（了解）  
局部变量：随着方法的进栈而诞生，随着方法出栈而消失  
成员变量：随着对象创建而诞生，随着对象被垃圾回收而消失  

```java
public class Demo{
    String name;//成员变量

    public void methodA)(){
        int num=20;//局部变量
        System.out.println(num);
        System.out.println(name);
    }

    public void methodB(int param){//方法的参数就是局部变量
        //参数在方法调用的时候，必然会被赋值
        System.out.ptintln(param);

        int age;//局部变量
        //System.out.println(age);//没赋值不能用
        //System.out.println(num);//错误写法
        System.out.println(name);
    }
}
```

## 面向对象的三个特征：封装，继承，多肽  

### 封装  

封装性在Java当中的体现：  
1、方法就是一种封装  
2、关键词private也是一种封装  

封装就是将一些细节信息隐藏起来，对于外界不可见  

#### private关键字的作用及使用  

问题描述：定义person的年龄时，无法阻止不合理的数值被设置进来。  
解决方案：用private关键字将需要保护的成员变量进行修饰  

一旦使用了private进行修饰，那么本类当中仍然可以随意访问。  
但是！超过了本类范围之外就不能再访问了。  

间接访问private成员变量，就是定义一对Getter/Setter方法  

必须叫setXxx或者是getXxx命名规则  
对于Getter来说，不能有参数，返回值类型和成员变量对应   
对于Setter来说，不能有返回值，参数类型和成员变量对应  

```java
public class Demo{
    String name;
    private int age;

    public void show(){
        System.out.println("我叫"+name+".年龄"+age);
    }

    //这个成员方法，专门用于向age设置数据
    public void setAge(int num){
        if (num<100&&num>=9){//如果是合理的情况
        age =num;
        }else{
            System.out,println("数据不合理");
        }
    }

    //这个成员方法，专门私语获得age的数据
    public int getAge(){
        return age;
    }
}
```

```java

public class Demo{
    public static void main(String[] age){
        Person person=new Person();
        person.show ();
        
        person.name="赵丽颖"；
        //person.age=-20;//直接访问private内容，错误写法
        person.setAge(-20);
        person.show();
               }
}
```

例题：练习用private关键字定义学生类  

对于基本类型当中Boolean值，Getter方法一定要写成isXxx的形式，而setXxx规则不变。  

```java 
public class Demo{

    private String name;//姓名
    private int age;//年龄
    private boolean male;//是不是爷们

    public void setMale(boolean b){
        male = b;
    }

    public boolean isMale(){
        return male;
    }

    public void setName(String name){
        name=str;
    }

    public String getName(){
        return name;
    }

    public void setAge(int age){
        age=num;
    }

    public int getAge(){
        return age;
    }
}
```

```java
public class Demo{
    public static void main(String[] age){
        Student stu=new Student();

        stu.setName("鹿晗");
        stu.setAge(20);
        stu.setMale(tute)

        System.out.println("姓名:"+stu.getName());
        System.out.println("年龄"+stu.getAge());
        System.out.println("是不是爷们"+stu.isMale());
    }
}
```

##### this关键词的作用  

当方法的局部变量和类的成员变量重名的时候，根据“就近原则”，优先使用局部变量  
如需要访问本类的成员变量，需要使用格式  
this.成员变量名  

“通过谁调用的方法，谁就是this”   

```java
public class Person{
    String name;//我自己的名字  

    //参数name是对方的名字
    //成员变量name是自己的名字
    public void sayHello(String name){
        System.out.println(name+",你好，我是"+this.name);
    }
}
```

```java
public class Demo{
    public static void main(String[] args){
        Person person=new Person();
        //设置我的名字
        person.name="王健林";
        person.sayHello(/*name:*/"王思聪")
    }
}
```

##### 构造方法  

构造方法是专门用来创建对象的方法，当我们通过关键字new来创建对象时，其实就是再调用构造方法  
格式：
public 类名称（参数类型 参数名称）{
    方法体
}

注意事项：  
1、构造方法的名称必须和所在类型名称完全一样，就连大小写也要一样  
2、构造方法不要写返回值类型，连void都不写  
3、构造方法不能return一个具体的返回值  
4、如果没有编写任何构造方法，那么编译器将会默认赠送一个构造方法，没有参数，方法体什么事都不做。  
public Student（）{}
5、一旦编写了至少一个构造方法，那么编译器将不再赠送  
6、构造方法也是可以进行重载的。  
重载：方法名称相同，参数列表不同  

```java 
public class Student {

    //成员变量
    private String name;
    private int age;

    //无参数的构造方法
    public Student(){
        System.out.println("无参数构造方法执行啦!");
    }

    //全参数的构造方法
    public Student (String name,int age){
        System.out.println("全参数构造方法执行啦~");
        this.name=name;
        this.age=age;
    }
    
    //Getter  Setter
    public void setName(String name){
        this.name = name;
    }

    public void getName(){
        return name;
    }

    public void setAge(int age){
        this.age = age;
    }

    public void getAge(){
        return age;
    }
    }
```

```java 
public class Demo{
    public static void main(String[] args){
        Student stu1 = new Student();//无参数
        System.out.println("=============");

        Student stu2 = new Student(/*name:*/"赵丽颖",/*age*/20);//全参构造
        System.out.println("姓名"+stu2.getName()+",年龄"+stu2.getAge());
        //如果需要改变对象当中的成员变量数据内容，仍然还需要使用setXxx方法
        stu2.setAge(21);//改变年龄
        System.out.pringln("姓名:"+stu2.getName()+".年龄："+stu2.getAge());
    }
}
```

 ### 继承

#### 概述  

  面向对象的三大特征：封装性、继承性、多态性  
  继承是多态的前提，如果没有继承，就没有多态  
  继承主要解决的问题就是：共性抽取  

  继承关系当中的特点：  
  1、子类可以拥有父类的“内容”  
  2、子类还可以拥有自己专有的内容  

  父类也可以叫基类，超类  
  子类也可以叫派生类  

#### 继承后特点

##### 成员变量  

 在父子类的继承关系当中，如果成员变量重名，则创建子类对象时，访问有两种方式  

直接通过子类对象访问成员变量  
     等号左边是谁，就优先用谁，没有则向上找  
间接通过成员方法访问成员变量  
     该方法属于谁，就优先用谁，没有则向上找  

```java
public class Fu{
    int numFu = 10;
    int num = 100;
    public void methodFu(){
        //使用的是本类当中的，不会向下找
        System.out.println(num);
    }
}

public class Zi extends Fu{
    int numZi = 20;
    int num = 200;

    public void methodZi(){
        //因为本类当中有num，所以这里用的是本类num
        System.out.println(num);
    }
}

public class Demo01ExtendsFile{
    public static void main(String[] args){
        Fu fu = new Fu();//创建父类对象
        System.out.println(fu.numFu);//只能使用父类的东西，没有任何子类的内容
        System.out.println("===============");

        Zi zi = new Zi();
        System.out.println(zi.numFu);//10
        System.out.println(zi.numZi);//20
        System.out.println("=================");

        //等号左边是谁，就优先谁
        System.out.println(zi.num);//优先子类，200
        //System.out.println(zi.abc);到处都没有，编译器报错
        System.out.println("====================");

        //这个方法是子类的，优先用子类，没有再向上找
        zi.methodZi();//200
        //这方法是再父类当中定义的
        zi.methodFu();//100
    }
}
```

* 区分子类方法中重名的三种变量  

局部变量：       直接写成员变量名  
本类的成员变量    this.成员变量名  
父类的成员变量名  super.成员变量名  

```java
public class Fu{
    int num = 10;
}

public class Zi{
    int num = 30;

    public void method(){
        int num = 30
        System.out.println(num);//30,局部变量
        System.out.println(this.num);//20,本类的成员变量
        System.out.println(super.num);//10,父类的成员变量
    }
}

public class Demo01ExtendFild{
    public static void main(String[] args){
        Zi zi = new Zi();

        zi.method();
    }
}
```

##### 成员方法  

在父类的继承关系中，创建子类对象，访问成员方法的规则  
    创建的对象是谁，就优先用谁，如果没有，则向上找  

###### 成员方法不重名：  
```java
class Fu{ 
    public void show(){ 
    System.out.println("Fu类中的show方法执行"); 
    }
}

class Zi extends Fu{ 
    public void show2(){ 
    System.out.println("Zi类中的show2方法执行"); 
    } 
}

public class ExtendsDemo04{ 
    public static void main(String[] args) { 
    Zi z = new Zi(); //子类中没有show方法，但是可以找到父类方法去执行
    z.show(); z.show2(); 
    } 
}
```

###### 成员方法重名----重写（Override）  

概念：在继承关系中，方法的名称一样，参数列表也一样。  

重写（Override）：方法名称一样，参数列表【也一样】。覆写，覆盖  
重载（Overload）：方法名称一样，参数列表【不一样】。  

方法的覆盖重写的特点：创建的是子类对象，则优先用子类方法。

```java
public class Fu{
    public void methodFu(){
        System.out.println("父类方法执行了");
    }
    public void method(){
        System.out.println("父类重名方法执行啦~");
    }
}

public class Zi{
    public void methodZi(){
        System.out.println("子类方法执行了");
    }
    public void method(){
        System.out.println("子类重名方法执行啦~");
    }
}

public class Demo{
    public static void main(Stirng[] args){
        Zi zi = new Zi();

        zi.methodFu();
        zi.methodZi();

        //创建的是new了子类对象，所以优先使用子类方法
        zi.method();
    }
}
```

注意事项：  

1、必须保证父子类之间的方法的名称相同，参数列表也相同  
@Override：写在方法前面，用来检测是不是有效的正确覆盖重写  
这个注释就算不写，只要满足要求，也是正确的方法覆盖重写  

2、子类方法的返回值必须【小于等于】父类的方法的返回值类型  
小扩展提示：java.lang.Object类是所有类的公共最高父类（祖宗类），java.lang.String就是Object的子类  

3、子类的方法的权限必须【大于或等于】父类的方法的权限修饰符  
小扩展提示：public>protected>(default)>private  
备注：(default)不是关键字default，而是什么都不写，留空  

重写-应用场景  

```java
class Phone { 
    public void sendMessage(){ 
        System.out.println("发短信"); 
        }
        public void call(){ 
            System.out.println("打电话"); 
        }
        public void showNum(){ 
            System.out.println("来电显示号码"); 
        } 
}

//智能手机类 
class NewPhone extends Phone { 
    //重写父类的来电显示号码功能，并增加自己的显示姓名和图片功能 
    public void showNum(){ 
        //调用父类已经存在的功能使用
        super super.showNum(); 
        //增加自己特有显示姓名和图片功能 
        System.out.println("显示来电姓名"); 
        System.out.println("显示头像"); 
        } 
}

public class ExtendsDemo06 { 
    public static void main(String[] args) { // 创建子类对象 
    Phone phone = new Phone();
    phone.call();
    phone.send();
    phone.show();
    System.out.println("============");

    NewPhone newphone = new NewPhone();
    newphone.call();
    newphone.send();
    newphone.call();
    }
}
```

##### 构造方法  

继承关系中，父子的构造方法的访问特点：  

1、子类构造方法当中有一个默认隐含的"super()"调用，所以一定是先调用的父类构造，后构造的子类构造。  

2、子类构造方法可以通过super关键字来调用父类重载构造  

3、super的父类构造调用，必须是子类构造方法的第一个语句，不能一个子类构造调用多次super构造  

总结：  
子类必须调用父类的构造方法，不写则赠送super();写了则用写的指定的super调用，super只能有一个，还必须是第一个  

```java
package aemo03;

public class Demo03Constructor {
    public static void main(String[] args) {
        Zi zi = new Zi();

    }
}


public class Fu {
    public Fu(){
        System.out.println("父类无参构造方法！");
    }
    public Fu(int num) {
        System.out.println("父类有参构造方法！");
    }
}

public class Zi extends Fu{
    public Zi(){
        super(10);
        System.out.println("子类构造方法");
    }
    public void method(){
        //super();错误写法，只有子类的构造方法，才能调用父类构造方法
    }
}
```



#### 继承的三个特点   

1、 Java只支持单继承，不支持多继承。  

```java
//一个类只能有一个父类，不可以有多个父类。 
class C extends A{} //ok 
class C extends A，B... //error
```

2、 Java支持多层继承(继承体系)。  

```java
class A{} 
class B extends A{} 
class C extends B{}
//顶层父类是Object类。所有的类默认继承Object，作为父类
```

3、一个子类的直接父亲是唯一的，但是一个父类可以拥有很多个子类  
   可以有很多兄弟姐妹

#### 抽象类

##### 抽象方法和抽象类的格式和使用  

抽象方法：就是加上abstract关键字，然后去掉大括号，直接分号结束  
抽象类：抽象方法所在的类，必须是抽象类才行，在class之前写上abstract即可。  

如何使用抽象类和抽象方法：  
1、不能直接创建new抽象类对象  
2、必须用一个子类来继承抽象父类  
3、子类必须覆盖重写父类当中所有的抽象方法  
覆盖重写(实现)；子类去掉抽象方法的abstract关键字，然后补上方法体大括号  


```java
public abstract class Animal{
    //这是一个抽象方法，代表吃东西，但是具体吃什么(大括号的内容)不确定  
    public abstract void eat();

    //这是普通的成员方法
   // public void normalMethod(){

    }
    }

public class Cat extends Animal{
    @override
    public void eat(){
        System.out.println("猫吃鱼");
    }
}

public class DemoMain{
    public static void main(String[] args){
        //Animal animal = new Animal();//错误写法，不能直接创建抽象类对象  
        Cat cat = new Cat();
        cat.eat();
    }
}
```

#### 接口

##### 接口的内容

接口就是多个类的公共规范  
接口是一种引用数据类型，最重要的内容就是其中的：抽象方法  

如何定义一个接口的格式  
public interface 接口名称 {
    //接口内容
}  
备注：换成了关键字interface之后，编译的字节代码仍然是：.java-->.class  

如果是java7，那么接口可以包含的内容有：  
1、常量，格式  
[public] [static] [final] 数据类型 常量名称 = 数据值；
注意：  
常量必须进行赋值，而且一旦赋值，不可改变  
常量名称完全大写，用下划线进行分隔  

2、抽象方法 格式  
[public] [static] [final] 返回值类型 方法名称(参数列表)；  
注意：实现类必须覆盖重写接口所有的抽象方法，除非实现类是抽象类  

如果是Java8，还可以额外有：  
3、默认方法  格式  
[public] default 返回值类型 方法名称(参数列表) {方法体}  
注意：默认方法也可以被覆盖重写  

4、静态方法  格式  
[public] static 返回值类型 方法名称() {方法体}  
注意：应该通过接口名称进行调用，不能通过实现类对象调用接口静态方法  

如果是Java9，还可以额外包含有：  
5、私有方法 格式  
普通私有方法：private 返回值类型 方法名称(参数列表){方法体}  
静态私有方法：private static 返回值类型 方法名称(参数列表) {方法体}  
注意：private的方法只有接口自己才能调用，不能被实现类或者别人使用  


##### 抽象方法 

在任何版本的Java中，接口都能定义抽象方法  

格式：  
public abstract 返回值类型 方法名称(参数列表)；  

注意事项：  
1、接口当中的抽象方法，修饰符必须是两个固定的关键字，public abstract  
2、这两个关键字修饰符，可以选择性的省略。  
3、方法三要素，可以随意定义  

```java  
public interface MyInterfaceAbs{
    //这是一个抽象方法 
    public abstract void methodAbs1();
    //这也一个抽象方法 
    abstract void methodAbs2();
    //这也一个抽象方法 
    public void methodAbs3();
    //这也一个抽象方法 
    void methodAbs3();
}
```
  

1、接口不能直接使用，必须有一个“实现类”，来“实现”该接口  
格式  
public class 实现类名称 implement 接口名称{
    //...
}  
2、接口的实现必须覆盖重写(实现)接口中所有的抽象方法  
实现：去掉abstract关键字，加上方法体大括号  
3、创建实现类的对象，进行使用  

注意事项：  
如果实现类并没有覆盖重写接口的所欲抽象方法，那么这个实现类就必须是抽象类  

```java
//定义接口类
public interface LiveAble { 
    // 定义抽象方法 
    public abstract void eat(); 
    public abstract void sleep();
     }

//定义实现类
public class Animal implements LiveAble { 
    @Override public void eat() { 
        System.out.println("吃东西"); 
        }
    @Override public void sleep() { 
        System.out.println("晚上睡"); 
        } 
}

//定义测试类
public class InterfaceDemo { 
    public static void main(String[] args) { 
        // 创建子类对象 
        Animal a = new Animal(); 
        // 调用实现后的方法 
        a.eat(); 
        a.sleep(); 
        } 
    }
```

##### 默认方法  

从java8开始，接口里允许定义默认方法。  
格式：  
public default 返回值类型 方法名称(参数列表){
    方法体
}  
备注：接口当中的默认方法，可以解决接口升级的问题  

1、接口的默认方法，也可以通过接口的实现类对象，直接调用  
2、接口的默认方法，也可以被接口实现类进行覆盖重写  


```java
//这是接口类
public interface MyInterfaceDefault {
    //抽象方法
    public abstract  void methodAbs();

    //新添加的方法，改成默认方法
    public default void methodAbs2(){
        System.out.println("这是新添加的默认方法");
    }
}

//这是实现类
//实现类A
public class MyInterfaceDefaultA implements MyInterfaceDefault{
    @Override
    public void methodAbs() {
        System.out.println("实现了抽象方法，aaa");
    }
}

//实现类B
public class MyInterfaceDefaultB implements MyInterfaceDefault{
    @Override
    public void methodAbs() {
        System.out.println("实现了抽象方法，BBB");
    }

    @Override
    public void methodAbs2() {
        System.out.println("覆盖重写了接口的默认方法");
    }
}

//测试类
public class Demo10default {
    public static void main(String[] args) {
        //创建实现类对象
        MyInterfaceDefaultA a = new MyInterfaceDefaultA();
        a.methodAbs();
        a.methodAbs2();

        System.out.println("=============");
        MyInterfaceDefaultB b = new MyInterfaceDefaultB();
        b.methodAbs();
        b.methodAbs2();
    }
}
```

##### 静态方法  

注意事项：不能通过接口实现类的对象来调用接口当中的静态方法  
正确用法：通过接口名称，直接调用其中的静态方法  
格式：  
接口名称.静态方法(参数)；  

```java
//接口类
public interface LiveAble { 
    public static void run(){
         System.out.println("跑起来~~~"); 
         }
     }

//实现类  
public class Animal implements LiveAble { 
    // 无法重写静态方法
 }

 //测试类  
public class InterfaceDemo { 
    public static void main(String[] args) { 
        // Animal.run(); // 【错误】无法继承方法,也无法调用
         LiveAble.run(); // 直接通过接口名称调用静态方法
         }
         }
```

##### 私有方法  

问题描述：  
我们需要抽取一个共有方法，用来解决两个默认方法之间重复代码的问题  
但是这个共有方法不应该让实现类使用，应该是私有化的  

解决方案：  
从Java 9开始，接口当中允许定义私有方法。  
1.普通私有方法，解决多个默认方法之间重重复代码问题  
格式：private 返回值类型 方法名称(参数列表){
    方法体
}  

2、静态私有方法，解决多个静态方法之间重复代码问题  
格式：  
private static 返回值类型 方法名称(参数列表){
    方法体
}  
```java
public interface LiveAble { 
    default void func(){ 
        func1(); 
        func2(); }
        private void func1(){ 
            System.out.println("跑起来~~~");
         }
        private void func2(){ 
            System.out.println("跑起来~~~"); 
        }
}
```

##### 常量定义和使用  

接口当中也可以定义“成员变量”，但是必须使用public static final三个关键字进行修饰  
从效果上看，这其实就是接口【常量】。  
格式：  
public static final 数据类型 常量名称 = 数据值；  
备注：  
一旦使用final关键字进行修饰，说明不可改变  

注意事项：  
1、接口当中的常量，可以省略public static final，注意，不写也照样是这样  
2、接口当中的常量，必须进行赋值，不能不赋值   
3、接口中的常量命名，使用完全大写的字母，用下划线进行分隔。(推荐命名规则)  

```java
public interface MyInterfaceConst{
    //这其实就是一个常量，一旦赋值，不可以修改  
    public static final int NUM_OF_MY_CLASS = 12;
}

public class Demo05Interface{
    public static  void main(String[] args){
        //访问接口当中的常量
        System.out.println(MyInterfaceConst.NUM_OF_MY_CLASS);
    }
}
```

##### 接口的多继承  

抽象方法：接口中，有多个抽象方法时，实现类必须重写所有抽象方法。如果抽象方法有重名的，只需要重写一次。  

默认方法：接口中，有多个默认方法时，实现类都可继承使用。如果默认方法有重名的，必须重写一次。  

静态方法：接口中，存在同名的静态方法并不会冲突，原因是只能通过各自接口名访问静态方法。  

注意事项：  
1、接口是没有静态代码块或者构造方法的  
2、一个类的直接父类是唯一的，但是一个类可以同时实现多个接口  

格式：  
public class MyInterfaceImp implements MyInterfaceA,MyInterfaceB{
    //覆盖重写多有的抽象方法
}  

3、如果实现类所实现的多个接口当中，存在重复的抽象方法，那么只需要覆盖重写一次即可  
4、如果实现类没有覆盖重写所有接口当中的所有抽象方法，那么实现类就必须是一个抽象类  
5、如果实现类锁实现的多个接口当中，存在重复的默认方法，那么实现类一定要对冲突的默认方法进行覆盖重写  
6、一个类如果直接父类当中的方法，和接口当中的默认方法产生冲突，优先用父类当中的方法  

```java
class 类名 [extends 父类名] implements 接口名1,接口名2,接口名3... { 
    // 重写接口中抽象方法【必须】 
    // 重写接口中默认方法【不重名时可选】 
}
```
 

1、类与类之间是单继承的，直接父类只有一个   
2、类与接口之间是多实现的，一个类可以实现多个接口  
3、接口和接口之间是多继承的  

注意事项：  
1、多个父类接口当中的抽象方法如果重复，没关系  
2、多个父类接口当中的默认方法如果重复，那么子接口必须进行默认方法的覆盖重写。【而且带着default关键字】  

```java
//定义接口类 
interface A { 
    public default void method(){ 
        System.out.println("AAAAAAAAAAAAAAAAAAA");
         } 
         }
         interface B { 
             public default void method(){ 
                 System.out.println("BBBBBBBBBBBBBBBBBBB"); 
                 } 
}
```

### 多态  

#### 格式与使用  

代码当中体现多态性，其实就是一句话：父类引用指向子类对象。  

格式：  
父类名称 对象名 = new 子类名称();  
或者  
接口名称 对象名 = new 实现类名称();  

```java
public class Demo01Multi{
    public static void main(String[] args){
        //使用多态写法
        //左侧父类的使用，指向了右侧子类的对象  
        Fu obj = new Zi();

        obj.method();
        obj.methodFu();
    }
}

public class Fu{
    public void method(){
        System.out.println("父类方法");
    }
    public void methodFu(){
        System.out.prontln("父类特有方法");
    }
}

public class Zi extends Fu{
    @override
    public void method(){
        System.out.println("子类方法");
    }
}
```

#### 成员变量的使用特点  

访问成员变量的两种方式：  

1、直接通过对象名称访问成员变量，看等号左边是谁，优先用谁，没有则向上找  
2、间接通过成员方法访问成员变量，看该方法属于谁，优先用谁，没有则想上找   

对比：  
成员变量：编译看左边，运行还看左边  
成员方法：编译看左边，运行看右边

```java 
//父类
public class Fu {
    int num = 10;

    public void showname(){
        System.out.println(num);
    }
}

//子类
public class Zi extends Fu{
    int num = 20;

    @Override
    public void showname() {
        System.out.println(num);
    }
}

public class Demo01MultiField {
    public static void main(String[] args) {
        //使用多态的写法，父类指向子类对象
        Fu obj = new Zi();
        System.out.println(obj.num);

        System.out.println("========");

        obj.showname();//子类没有覆盖重写就是Fu：10
        //子类如果覆盖重写了，就是20
    }
}
```

#### 使用多态的好处   

员工：work():抽象<---extends或者implements---讲师类work(){讲课}  
员工：work():抽象类<---extends或者implements---助教类work(){辅导}  

如果不用多态：只用子类，那么写法是  
Teacher one = new Teacher();  
one.work();//讲课  
Asistent two = new Teacher();  
two.work();//辅导  

现在唯一要做的事情是调用work方法，其他不关心  

使用多态的写法  
Employee one = new Teacher();  
one.work();//讲课  
Employee two = new Teacher();  
two.work();//辅导  

* 1、好处：无论右边new的时候换成了哪个子类对象，等号左边的调用方法都不会变化  

#### 引用类型转换

##### 对象的向上转型  

1、对象的向上转型，其实就是多态写法：  
格式：父类名称 对象名 = new 子类名称();  
      Animal animal = new Cat();  
含义：右侧创建一个子类对象，把它当作父类来看待使用，  
      创建了一只猫，当作动物看待，没问题  

注意事项：向上转型一定是安全的，从小范围转向了大范围，从小范围的猫，向上转型成为更大的动物  

##### 对象的向下转型  

2、对象的向下转型，其实是一个【还原】的动作  
格式：子类名称 对象名 = (子类名称) 父类对象；  
含义：将父类对象，【还原】成员本来的子类对象  

Animal animal = new Cat();//本来是猫，向上转型成为动物  
Cat cat = (Cat) animal;//本来是猫，已经别当成动物了，还原成本来的样子  

注意事项：  
a、必须保证对象本来创建的时候，就是猫，才能向下转型成为猫  
b、如果对象创建的时候本类不是猫，现在非要向下转型成为猫，就会报错  classCastException  

####  用instanceof关键字进行类型判断  

如何才能知道一个父类引用的对象，本来是什么子类？  

格式：  
对象 instanceof 类名称  
这将会得到一个Boolean值结果，也就是判断前面的对象能不能当作后面类型的实例  

```java
public class Test { 
    public static void main(String[] args) { 
    // 向上转型 
    Animal a = new Cat(); a.eat(); 
    // 调用的是 Cat 的 eat 
    // 向下转型 
        if (a instanceof Cat){ 
        Cat c = (Cat)a;
        c.catchMouse();
        // 调用的是 Cat 的 catchMouse 
    } 
        else if (a instanceof Dog){ 
        Dog d = (Dog)a; 
        d.watchHouse(); // 调用的是 Dog 的 watchHouse 
} 
} 
    public static void giveMePet(Animal animal){
        if (animal instanceof Dog){
            Dog dog = (Dog) animal;
            dog.watchHouse;
        }
        if (a instanceof Cat){ 
        Cat c = (Cat)a;
         c.catchMouse();
          // 调用的是 Cat 的 catchMouse 
    } 
    }
        }
```

### API概述和使用步骤  

概述：API（Application Programming Interface），应用程序编程接口，java API是一本程序员的字典，是JDK中提供给我们使用的类的说明书，这些类将底层的代码实现封装了起来，我们不需要关心这些类是如何实现的，只需要学习这些类如何使用即可，所以我们可以通过查询API的方式，来学习java提供的类，并得知如何使用

## super和this关键字  

### super关键字的三种用法  

1、在子类的成员方法，访问父类的成员变量  
2、在子类的成员方法，访问父类的成员方法  
3、在子类的构造方法，访问父类的构造方法  

### this关键字的三种用法  

super关键字用来访问父类内容，而this关键字用来访问本类内容，用法也有三种。  

1、在本类的成员方法，访问本类的成员变量  
2、在本类的成员方法，访问本类的另一个成员方法  
3、在本类的构造方法，访问本类的另一个构造方法。  

在第三种用法当中要注意：  

A、this(...)调用也必须是构造方法的第一个语句，唯一一个  
B、super和this两种构造调用，不能同时使用  

## Scanner,Random,ArrayList的使用

### Scanner概述及其API文档的使用  

Scanner类的功能；可以实现键盘输入的数据，到程序当中  

引用类型的一般使用步骤  

1、导包  
import 包路径.类名称；  
如果需要使用的目标类，和当前类位于同一个包下，则可以省略导包语句不写。  
只有java.lang包下的内容不需要导包，其他的包都需要import语句  

2、创建  
类名称 对象名 = new 类名称（）；  

3、使用  
对象名.成员方法名();  

获取键盘输入的一个int数字，int num = sc.nextInt();
获取键盘输入的一个字符串，String str = sc.next();

```java
package cn.itcase.day07.demo01;

import java.until.Scanner;//导包  

public class Demo{
    public static void main(String[] args){
        //2、创建  
        //备注：System.in代表从键盘进行输入  
        Scanner sc = new Scanner(System.in);

        //3、获取键盘输入的int数字  
        int num = sc.nextInt();
        System.out.println("输入的int数字是："+num);

        //4、获取键盘输入的字符串
        String str = sc.next();
        System.out.println("输入的字符串是："+str);
    }
}
```

#### Scanner例题  

题目：  
键盘输入两个int数字，并且求出和值   

思路：  
1、既然需要键盘输入，那么就要用Sacnner  
2、Scanner的三个步骤，导包，创建，使用  
3、需要的是两个数字，所以要调用两次的nextInt方法  
4、得到了两个数字，就需要加在一起  
5、将结果打印输出  

```java
package cn.itcast.day07.demo01;

import java.util.Scanner;

public class Demo{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int b = sc.nextInt();

        int result = a+b;
        System.out.println("结果是"+result);
    }
}
```

例题二：  
输入三个int数字，然后求出其中的最大值  

```java
import java.util.Scanner;

public class demo{
    public static void main(String[] args){
        Scanner sc =new Scnaner(System.in);

        System.out.println("请输入第一个数字");
        int a = sc.nextInt();
         System.out.println("请输入第二个数字");
        int b = sc.nextInt();
         System.out.println("请输入第三个数字");
        int c = sc.nextInt();

        //首先得到前面两个数字当中的最大值
        int temp = a>b?a:b;
        int max=temp>c?temp:c;
        System.out.println("最大值是："+max);
            }
}
```

### Rondom的概述和基本使用  

Random类用来生成随机的数字，使用起来也是三个步骤；  

1、导包  
import java.util.Random;  

2、创建  
Random r = new Random();//小括号当中留空即可  

3、使用  
获取一个随机的int数字（范围是int所有的范围，有正负两种），int num = r.nextInt()  
获取一个随机的int数字（参数代表了范围，左闭右开区间），int num = r.nextInt(3)  
实际上代表的含义是：[0,3),也就是0~2

```java
public class Demo{
    public static void main(String[] args){
        Random r = new Random();

        int num = r.nextInt();
        System.out.println("随机数字是："+num);
    }
}
```

```java
public class Demo{
    public static void main(String[] args){
        Random r = new Random();

        for(int i=0;i<100;i++){
            int num = r.nextInt(/*bound:*/10);//范围实际上是0~9
            System.out.println(num);
        }
    }
}
```

例题：  
题目要求：  
根据int变量n的值，来获取随机数字，范围是[1,n),可以取到1也可以取到n；  

思路：  
1、定义一个int变量n，随机赋值  
2、要使用Random：三个步骤，导包，创建，使用  
3、如果写10，那么就是0~9，然而想要的就是1~10，可以发现：整体+1即可。  
4、打印随机数字  

```java 
public class Demo{
    public static void main(String[] args){
        int n = 5;
        Random r = new Random();

        for(int i=0;i<100;i++){
            //本来范围是[0,n),整体+1之后变成了[1,n+1),也就是[1,n]
            int result = r.nextInt(n);
            System.out.println(result);
        }
    }
}
```

Random练习二，猜数字小游戏  
题目：  
用代码模拟猜数字的小游戏。  

思路：  
1、首先需要产生一个随机数字，并且一旦产生不再变化，用Random的nextInt的方法  
2、需要键盘输入，所以用到了Scanner  
3、获取键盘输入的数字，用Scanner当中的nextInt方法  
4、已经得到了两个数字，判断（if）一下；  
   如果太大了，提示太大，并且重试  
   如果太小了，提示太小，并且重试   
   如果猜中了，游戏结束  
5、重试就是再来一次，循环次数不确定，用while（true).  

```java
public class demo{
    public static void main(String[] args){
        Random r = new Random();
        int randomNum = r.nextInt(/*bound:*/100)+1;//[1,100]
        Scanner sc = new Scanner(System.in);

        while (true){
            System.out.println("请输入你猜测的数字：");
            int guessNum = sc.nextInt();//键盘输入猜测的数字

            if (guessNum>randomNum){
                System.out.println("太大了，请重试");
            }else if (guessNum<randomNum){
                System.out.println("太小了，请重试");
            }else{
                System.out.println("恭喜你，猜对了");
                break;
            }
        }
        System.out.println("游戏结束");
    }
}
```

### ArrayList 

#### 对象数组

题目：  
定义一个数组，用来存储3个Person对象。  

数组有一个缺点，一旦创建，程序运行期间长度就不可以发生改变。  

```java
public class Student {

    //成员变量
    private String name;
    private int age;

    //无参数的构造方法
    public Student(){
        System.out.println("无参数构造方法执行啦!");
    }

    //全参数的构造方法
    public Student (String name,int age){
        System.out.println("全参数构造方法执行啦~");
        this.name=name;
        this.age=age;
    }
    
    //Getter  Setter
    public void setName(String name){
        this.name = name;
    }

    public void getName(){
        return name;
    }

    public void setAge(int age){
        this.age = age;
    }

    public void getAge(){
        return age;
    }
    }
```

```java
public class Demo{
    public static void main(String[] args){
        //首先创建一个长度为3的数组，里面用来存放Person类型的对象  
        Person[] array = new Person[3];

        person one = new Person("迪丽热巴",18);
        person two = new Person("古力娜扎",28);
        person three= new Person("玛卡巴卡",38);

        //将one的当中的地址值赋值到数组的0号元素位置  
        array[0] = one;
        array[1] = two;
        array[2] = three;

        System.out.println(array[0]);//地址值
        System.out.println(array[1]);//地址值
        System.out.println(array[2]);//地址值

        System.out.println(array[1].getName());//古力娜扎
    }
}
```

#### 概述和基本使用  
   
数组的长度不可以发生改变。  
但是ArrayList集合的长度是可以改变的  

对于ArrayList来说，有一个尖括号<E>代表泛型  
泛型：也就是装在集合当中的所有元素，全都是统一的什么类型  
注意：泛型只能是引用类型，不能是基本类型  

注意事项：  
对于ArrayList集合来说，直接打印得到的不是地址值，而是内容  
如果内容留空，得到的是空的中括号[]  

```java
public class Demo{
    public static void main(String[] args){
        //创建了一个ArrayList集合，集合的名称是List，里面装的全都是String字符串类型的数据  
        //备注，从JDK 1.7开始，右侧的尖括号可以不写内容，但是<>本身还是要写的  
        ArrayList<String> list = new ArrayList<>();
        System.out.println(list);//[]

        //向集合当中添加一些数据，需要用到add方法。
        List.add("bob");
        System.out.println(list);//bob

        List.add("lisa");
        List.add("lily");
        List.add("john");
        System.out.println(list);

        //List.add(100);错误写法！因为创建的时候尖括号的泛型已经说明了是字符串，添加进去的元素必须是字符串
            }
}
```

#### 常用方法

public boolean add(E e);向集合当中添加元素，参数的类型和泛型一致，返回值代表是否添加成功。  
备注：对于ArrayList集合来说，add添加动作一定是成功的，所以返回值可用可不用。  
但是对于其他集合(今后学习)来说，add添加动作不一定成功。  

public E get(int index),从集合当中获取元素，参数是索引编号，返回值就是对应位置的元素  

public E remove(int index)；从集合当中删除元素，参数就是索引编号，返回值就是被删除掉的元素  

public int size(); 获取集合的尺寸长度，返回值就是集合中包含的元素个数  

```java 
public class Demo{
    public static void main(String[] args){
        ArrayList<String> List = new ArrayList<>();
        System.out.println(list);//[]

        //向集合中添加元素；add
        boolean success = list.add("刘岩");
        System.out.println("添加的动作是否成功"+success);//treu

        list.add("高圆圆");
        list.add("赵又廷");
        list.add("李小璐");
        list.add("贾乃亮");
        System.out.println(list);//[刘岩，高圆圆，赵又廷，李小璐，贾乃亮]

        //从集合获取元素，get。索引值从0开始
        String name = list.get(2);
        System.out.println("第二号索引位置"+name);

        //从集合中删除元素，remove，索引值从0开始
        String whoRemoved =list.remove(3);
        System.out.println("被删除的人是："+whoRemove);//李小璐
        System.out.println(list);//[刘岩，高圆圆，赵又廷，贾乃亮]

        //获取集合的长度尺寸，也就是其中的元素的个数  
        int size = list.size();
        System.out.println("集合的长度是："+size);

    }
}
```

#### 集合的遍历  

```java
import java.util.ArrayList;

public class Demo{
    public static void main(String[] args){
        ArrayList<String> list = new ArrayList<>();
        list.add("迪丽热巴");
        list.add("古力娜扎");
        list.add("玛卡巴卡");

        //遍历集合
        for(int i=0;i<list.size();i++){
            System.out.println(list.get(i));
        }
    }
}
```

#### 存储基本数据类型  

如果希望向集合ArrayList当中存储基本类型数据，必须使用基本类型对应的“包装类”。

基本类型          包装类（引用类型，包装类都位于java.lang包下）   
byte              Byte  
short             Short  
int               Int  
lang              Lang  
float             Float  
double            Double  
char              Character  
boolean           Boolean  

从JDK1.5开始，支持自动装箱，自动拆箱  
自动装箱：基本类型 -->包装类型  
自动拆箱：包装类型 -->基本类型

```java  
public class Demo{
    public static void main(String[] args){
        ArrayList<String> listA=new ArrayList<>();
        //错误写法！泛型只能是引用类型，不能是基本类型  
        //ArrayList<int> listB = new Arraylist<>();

        ArrayList<Integer> listC = new  ArrayList<>();
        listC.add(100);
        listC.add(200);
        System.out.println(listC);//[100,200]

        int num = listC.get(1);
        System.out.println("第一号元素是："+num);
    }
}
```

#### ArrayList练习一——存储随机数字  

题目：生成6个1~33之间的随机整数，添加到集合，并遍历集合。  

思路：  
1、需要存储6个数字，创建一个集合，<Integer>  
2、产生随机数，需要用到Random  
3、用循环6次，来产生6个随机数字：for循环  
4、循环内调用r.nextInt(int n),参数是33，0~32，整体+1才是1~33  
5、把数字添加到集合中：add  
6、遍历集合：for，size，get  

```java
package demo01;

import java.util.ArrayList;
import java.util.Random;

public class Demo01ArrayListRandom {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>();
        Random r =new Random();
        for(int i=0;i<6;i++){
            int num = r.nextInt(33)+1;
            list.add(num);
        }
        //遍历集合
        for(int i=0;i<list.size();i++){
            System.out.println(list.get(i));
        }
    }
}
```

#### ArrayList练习二——存储自定义对象  

题目：自定义4个学生对象，添加到集合，并遍历  

思路：  
1、自定义Student学生类，四个部分  
2、创建一个集合，用来存储学生对象，泛型：<Student>  
3、根据类，创建4个学生对象  
4、将4个学生对象添加到集合中，add  
5、遍历集合，for，size，get  

```java
package demo01;

public class Student {
    private String name;
    private int age;

    public Student() {
    }

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void setName(String name) {
        this.name = name;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }
}
```

```java
package demo01;

import java.util.ArrayList;

public class Demo02ArrayListStudent {
    public static void main(String[] args) {
        ArrayList<Student> list = new ArrayList<>();

        Student one = new Student("古力娜扎",20);
        Student two = new Student("迪丽热巴",21);
        Student three = new Student("马儿扎哈",23);
        Student four = new Student("玛卡巴卡",34);

        list.add(one);
        list.add(two);
        list.add(three);
        list.add(four);

        for (int i = 0; i < list.size(); i++) {
            Student stu = list.get(i);
            System.out.println("姓名"+stu.getName()+"年龄"+stu.getAge());
        }

    }
}
```

#### ArrayList练习三——按指定格式遍历集合字符串  

题目：定义以指定格式打印集合的方法(ArrayList类型作为参数)，使用{}括起来集合，使用@分隔每个元素。  
格式参照{元素@元素@元素@}。  

System.out.println(list);   [10,20,30]  
printArrayList(list);   {10@20@30}


#### ArrayList练习四——筛选集合中的随机数  

题目：  
用一个大集合存入20个随机数字，然后筛选其中的偶数元素，放到小鸡和当中  
要求使用自定义的方法来实现筛选。  

分析：  
1、需要创建一个大集合，用来存储int数字，<Integer>  
2、随机数字就用Random nextInt  
3、循环20次，把随机数字放入大集合中，for循环，add方法   
4、定义一个方法，用来进行筛选。  
筛选：根据大集合，筛选符合要求的元素，得到小集合。  
三要素  
返回值类型:ArrayList小集合(里面元素个数不确定)  
方法名称：getSmalllist  
参数列表：ArrayList大集合（装着20个随机数字）  
5、判断（if）是偶数，num%2==0  
6、如果是偶数，就放到小集合当中，否则不放  

```java
package demo01;

import java.util.ArrayList;
import java.util.Random;

public class Demo04ArrayListReturn {
    public static void main(String[] args) {
        ArrayList<Integer> bigList = new ArrayList<>();
        Random r =new Random();
        for(int i=0;i<20;i++){
            int num = r.nextInt(100)+1;
            bigList.add(num);
        }
        ArrayList<Integer> smallList = getSmallList(bigList);
        for (int i = 0; i < smallList.size(); i++) {
            System.out.println(smallList.get(i));
        }
    }
    public static ArrayList<Integer> getSmallList(ArrayList<Integer> bigList){
        ArrayList<Integer> smalllist = new ArrayList<>();
        for (int i = 0; i < bigList.size(); i++) {
            int num = bigList.get(i);
            if(num%2==0){
                smalllist.add(num);
            }
        }
        return smalllist;
    }
}
```


## String类、static关键字、Arrays类、Math类  

### String类  

java.lang.String类代表字符串  
API当中说，Java程序中的所有字符串面值(如"abc")都作为此类的实例实现  
其实就是说，程序当中所有双引号字符串都是String类的对象。就算没有new，也照样是  

字符串的特点：  
1、字符串的内容永不可变，【重点】  
2、正是因为字符串不可变，所以字符串是可以共享的  
3、字符串的效果上相当于是char[]字符数组，但是底层原理是byte[]字节数组。  

#### 创建字符串常见的3+1种方式。  

三种构造方法:  
public String();创建一个空白字符串，不含任何内容。  
public String(char[] array);根据字符数组的内容，来创建对应的字符串  
public String(bytr[] array);根据字节数组的内容，来创建对应的字符串。  

一种直接创建：  
String str = "hello";右边直接用双引号   

```java
package demo01;

public class Demo01String {

    public static void main(String[] args) {
        //使用空参构造
        String str1 = new String();
        System.out.println("第一个字符"+str1);

        //使用字符数组创建字符串
        char[] Arraychar = {'a','b','c'};
        String str2 = new String(Arraychar);
        System.out.println("第二个字符："+str2);

        //使用字节数组创建字符串
        byte[] Arraybyte ={97,98,99};
        String str3 = new String(Arraybyte);
        System.out.println("第三个字符："+str3);

        //直接创建
        String str4 ="abc";
        System.out.println("第四个字符："+str4);
    }
}
```

#### 字符串的常量池  

字符串的常量池：程序当中直接写上的双引号字符串，就在字符串常量池中  

对于基本类型来说:==是进行数值的比较  
对于引用类型来说；==是进行【地址值】的比较  

```java
public class Demo{
    public static void main(String[] args){
        String str1 = "abc";
        String str2 = "abc";

        char[] charArray = {'a','b','c'};
        STring str3 = new String(charArray);

        System.out.println(str1==str2);
        System.out.println(str1==str3);
        System.out.println(str2==str3)；
    }   
}
```

#### 字符串的比较相关方法  

==是进行对象的地址值比较，如果确实需要字符串的内容的比较，可以使用两个方法  

public boolean equals(Object obj);参数可以是任何对象，只有参数是一个字符串并且内容相同的才会给true，否则返回false  

注意事项：  
1、任何对象都能用Object进行接收  
2、equals方法具有对称性，也就是a.equals(b)和b.equals(a)效果一样  
3、如果比较双方一个常量一个变量，推荐把常量字符串写在前面  
推荐："abc".equals(str)   不推荐：str.equals("abc")  

public boolean equalsIgnoreCase(String str);

```java
publicclassString_Demo01{publicstaticvoidmain(String[]args){
    //创建字符串对象
    Strings1="hello";
    Strings2="hello";
    Strings3="HELLO";
    //booleanequals(Objectobj):比较字符串的内容是否相同
    System.out.println(s1.equals(s2));//true
    System.out.println(s1.equals(s3));//false
    System.out.println("‐‐‐‐‐‐‐‐‐‐‐");//booleanequalsIgnoreCase(Stringstr):比较字符串的内容是否相同,忽略大小写
    System.out.println(s1.equalsIgnoreCase(s2));//true
    System.out.println(s1.equalsIgnoreCase(s3));//true
    System.out.println("‐‐‐‐‐‐‐‐‐‐‐");
    }
    }
```

#### 字符串的获取相关方法  
String当中与获取相关方法的常用方法有：  

public int length();获取字符串当中含有的字符个数，拿到字符串的长度  
public String contact（String str），将当前字符串和参数字符串拼接成功作为返回值新的字符串  
public char charAt(int index),获取指定索引位置的单个字符，（索引从0开始)  
public int indexOf(String str);查找参数字符串在本字符串当中手粗出现的索引位置，如果没有返回-1值  

```java
package demo01;

public class Demo02StringGet {
    public static void main(String[] args) {
        //获取字符串的长度
      int length =  "jdsihfhasdhfas".length();
        System.out.println("字符串的长度是："+length);

        //拼接字符串
        String str1="hello";
        String str2="world";
        String str3=str1.concat(str2);
        System.out.println(str3);//str1,str2原封不动

        //获取指定索引位置的单个字符
        char ch ="Hello".charAt(1);
        System.out./;/println("第一次索引的位置是："+ch);

        //查找参数字符串在本来字符串当中出现的第一次索引位置
        //如果根本没有，返回-1值
        String original = "HelloWorld";
        int index = original.indexOf("llo");
        System.out.println("第一次索引的位置"+index);//2
    }
}
```

#### 字符串的截取方法  

public String substring(int index);截取从参数位置一直到字符串末尾，返回新的字符串  
public String substring(int begin,int end);截取从bigin开始，一直到end结束，中间的字符串   
备注：[begin,end),包含左边，不包含右边

```java
package demo01;

public class Demo03Substring {
    public static void main(String[] args) {
        String str1 = "HelloWorld";
        String str2 = str1.substring(5);
        System.out.println(str1);//HelloWorld
        System.out.println(str2);//World
        System.out.println("=============");

        String str3 = str1.substring(4,7);
        System.out.println(str3);
        System.out.println("==============");

        String strA = "Hello";
        System.out.println(strA);
         strA = "Java";
        System.out.println(strA);
    }
}
```  

#### 字符串的转换相关方法  

String当中与转换相关的常用方法有：  

public char[] toCharArray();将当前字符串拆分成为字符串数组作为返回值  
public byte[] getBytes();获得当前字符串底层的字节数组。  
public String[] replace(CharSequence oldString,CharSequence newString);  
将所有出现的老字符串替换成为新的字符串，返回替换之后的结果新字符串  
备注：CharSequence意思就是说可以接受字符串类型

```java
package demo01;

public class Demo04StringConvert {

    public static void main(String[] args) {
        //转换成为字符数组
        char[] chars = "hello".toCharArray();
        System.out.println(chars[1]);//H
        System.out.println(chars.length);//5i
        System.out.println("============");

        //转换成为字节数组
        byte[] bytes = "abc".getBytes();
        for(int i= 0;i<bytes.length;i++){
            System.out.println(bytes[i]);
        }

        //字符串的内容转换
        String str1 = "how do you do";
        String str2 = str1.replace("o","*");
        System.out.println(str1);
        System.out.println(str2);
        System.out.println("=============");


    }
}
```

#### 分割字符串的方法  

public String[] aplit(String regex);按照参数的规则，将字符串切分成为若干部分  

注意事项:
split方法的参数其实是一个"正则表达式",今后学习  
今天要注意：如果按照英文句点“.”进行切分，必须写“\\.”(两个反斜杠)

```java
package demo01;

public class Demo05StringSplit {
    public static void main(String[] args) {
        String str1 = "aaa,bbb,ccc";
        String[] Array1 = str1.split(",");
        for(int i=0;i<Array1.length;i++){
            System.out.println(Array1[i]);
        }
        String str3 = "aaa.bbb.ccc";
        String[] Array2 = str3.split("\\.");
        for (int i = 0; i < Array1.length; i++) {
            System.out.println(Array2[i]);
        }
    }
}
```

#### 按指定格式拼接字符串  

题目：定义一个方法，把数组{1，2，3}按照格式拼接成一个字符串，格式参照如下；[word1#word2#word3#]  

```java
package demo01;

public class Demo06StringPractise {
    public static void main(String[] args) {
        int[] array = {1,2,3};
        String result = fromArrayToString(array);
        System.out.println(result);
    }
    public static String fromArrayToString(int[] array){
        String str = "[";
        for (int i = 0; i < array.length; i++) {
            if(i==array.length-1){
                str+="word"+array[i]+"]";
            }else{
                str+="word"+array[i]+"#";
            }
        }
        return  str;
    }
}
```

### 静态static

#### 静态static关键字修饰成员变量  

如果一个成员变量使用了static关键字，那么这个变量不再属于对象自己，而是属于所在的类，多个对象共享一份数据   

```java
package demo01;

public class Demo01StaticField {
    public static void main(String[] args) {
        Student one = new Student("郭金",19);
        one.room = "教室101";
        System.out.println("姓名："+one.getName()+"年龄+"+one.getAge()+"所在教室"+one.room+",学号"+one.getId());
        Student two = new Student("杨荣",18);
        System.out.println("姓名："+one.getName()+"年龄+"+one.getAge()+"所在教室"+one.room+",学号"+two.getId());
    }
}
```

```java
package demo01;

public class Student {
    private int id;//学号
    private String name;//姓名
    private int age;//年龄
    static String room;//所在教室
    private static int idCounter = 0;//学号计数器

    public Student() {
        this.id=idCounter++;
    }

    public Student(String name, int age) {
        this.name = name;
        this.age = age;
        this.id = ++idCounter;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

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
        this.age = age;
    }
}
```

#### 静态static关键字修饰成员方法  

一旦使用static修饰成员方法，那么这就成为了静态方法。静态方法不属于对象，而是属于类的  

如果没有static关键字，那么必须首先创建对象，然后通过对象才能使用它  
如果有了static关键字，那么不需要创建对象，直接就能通过类名称来使用它  

无论是成员变量，还是成员方法，如果有了static，都推荐使用类名称进行调用  
静态变量：类名称.静态变量  
静态方法:类名称.静态方法()  

注意事项：  
1、静态不能直接访问非静态  
原因：因为在内存中是【先】有的静态内容，【后】有的非静态内容  
“无人不知道后人，但是后人知道前人”  
2、静态方法当中不能用this。  
原因:this代表当前对象，通过谁调用的方法，谁就是当前对象  
3、根据类名称访问静态变量的时候，全程和对象就没关系，只和类有关系，在方法区。

```java
package demo02;

public class MyClass {

    int num;//成员变量
    static int numStatic;//静态变量

    //成员方法
    public void method(){
        System.out.println("这是一个成员方法。");
        //成员可以访问成员变量
        System.out.println(num);
        //成员可以访问静态变量
        System.out.println(numStatic);
    }

    //静态方法
    public static void methodStatic(){
        System.out.println("这是一个静态方法");
        //静态方法可以访问静态变量
        System.out.println(numStatic);
        //静态不能直接访问非静态【重点】
        //System.out.println(num);//错误
    }
}
```

```java
package demo02;

public class Demo02StaticMethod {
    public static void main(String[] args) {
        MyClass obj = new MyClass();//首先创建对象
        //然后才能使用没有static关键字的内容
        obj.method();

        //对于静态方法来说，可以通过对象名进行调用，也可以直接通过类名称来调用
        obj.methodStatic();//正确不推荐，这种写法在编译之后也会被Java翻译成“类名称，静态方法名”
        MyClass.methodStatic();//正确推荐

        //对于本来当中的静态方法，可以省略类名称
        myMethod();
        Demo02StaticMethod.myMethod();//完全等效
    }
    public static void myMethod(){
        System.out.println("自己的方法");
    }
}
```

#### 静态代码块  

静态代码块的格式是：  

public class 类名称{  
        static{  
        //静态代码块内容  
        }  
     }  
特点：当第一次用到本类时，静态代码块执行唯一的一次  

静态代码的典型用途：  
用来一次性的对静态成员变量进行赋值  

```java
package Demo02;

public class Demo04Static {
    public static void main(String[] args) {
        Person one = new Person();
        Person twe = new Person();
    }
}
```

```java
package Demo02;

public class Person {
    static {
        System.out.println("静态代码块执行啦~");
    }
    public Person(){
        System.out.println("构造方法执行啦");
    }
}
```


### Arrays数组工具类  

java.util.Arrays 此类包含用来操作数组的各种方法，比如排序和搜索等。其所有方法均为静态方法，调用起来 非常简单。  

#### 操作数组的方法  

public static String toString(int[] a) ：返回指定数组内容的字符串表示形式。(按照默认格式：[元素1，元素2...])  

```java
public static void main(String[] args) { 
    // 定义int 数组 
int[] arr = {2,34,35,4,657,8,69,9}; 
// 打印数组,输出地址值 
System.out.println(arr); // [I@2ac1fdc4 
// 数组内容转为字符串
 String s = Arrays.toString(arr);
  // 打印字符串,输出内容 
  System.out.println(s); // [2, 34, 35, 4, 657, 8, 69, 9] }
  ```


public static void sort(int[] a) ：对指定的 int 型数组按数字升序(从小到大)进行排序。  

```java
public static void main(String[] args) { 
    // 定义int 数组 
    int[] arr = {24, 7, 5, 48, 4, 46, 35, 11, 6, 2}; 
    System.out.println("排序前:"+ Arrays.toString(arr)); // 排序前:[24, 7, 5, 48, 4, 46, 35, 11, 6, 2]
    // 升序排序
     Arrays.sort(arr); 
     System.out.println("排序后:"+ Arrays.toString(arr));// 排序后:[2, 4, 5, 6, 7, 11, 24, 35, 46, 48] }
```


备注：  
1、如果时数值，sort默认按照升序从小到大  
2、如果是字符串，sort默认按照字母升序  
3、如果是自定义的类型，那么这个自定义的类需要有comparable或者comparator接口的支持）  

#### 字符串倒序排列  

请使用 Arrays 相关的API，将一个随机字符串中的所有字符升序排列，并倒序打印。  

```java
public class ArraysTest { public static void main(String[] args) { 
    // 定义随机的字符串 
    String line = "ysKUreaytWTRHsgFdSAoidq"; 
    // 如何进行升序排列：sort  
    //必须是一个数组，才能用array.sort方法  
    //String --> 数组，用toString
    char[] chars = line.toCharArray(); 
    // 升序排序 
    Arrays.sort(chars);
     // 反向遍历打印 
     for (int i = chars.length‐1; i >= 0 ; i‐‐) { 
         System.out.print(chars[i]+" "); // y y t s s r q o i g e d d a W U T S R K H F A 
         } 
         } 
         }
```

### Math数学工具类  

java.lang.Math 类包含用于执行基本数学运算的方法，如初等指数、对数、平方根和三角函数。类似这样的工具 类，其所有方法均为静态方法，并且不会创建对象，调用起来非常简单。  

#### 基本运算的方法  

public static double abs(double a) ：返回 double 值的绝对值。  
```java 
double d1 = Math.abs(‐5); //d1的值为5
```
public static double ceil(double a) ：向上取整  
```java
double d1 = Math.ceil(3.3); //d1的值为 4.0
```
public static double floor(double a) ：向下取整 
```java
 double d1 = Math.floor(3.3); //d1的值为3.0
 ```
public static long round(double a) ： 四舍五入  
```java
long d1 = Math.round(5.5); //d1的值为6.0
```
Math.PI代表近似的圆周率常量（double）  

#### Math练习：小学数学真题  

请使用 Math 相关的API，计算在 -10.8 到 5.9 之间，绝对值大于 6 或者小于 2.1 的整数有多少个？  

```java
public class MathTest { public static void main(String[] args) {
     // 定义最小值
     double min = ‐10.8; 
     // 定义最大值 
     double max = 5.9; 
     // 定义变量计数 
     int count = 0; 
     // 范围内循环 
     for (double i = Math.ceil(min); i <= max; i++) { 
         // 获取绝对值并判断 
         if (Math.abs(i) > 6 || Math.abs(i) < 2.1) { 
             // 计数 
             count++; 
             } 
             }
             System.out.println("个数为: " + count + " 个"); 
             } 
             }
```

## final关键字概念与四种用法  

final关键字代表最终，不可改变的  

常用的四种用法：  
1、可以用来修饰一个类  
2、可以用来修饰一个方法  
3、还可以用来修饰一个局部变量  
4、还可以用来修饰一个成员变量  

## 四种修饰权限修饰符  
 
 Java中有四种修饰符：  

修饰符|public|protected|(default)|private  
-------|------|----------|---------|------  
同一个类|yes|yes|yes|yes  
同一个包|yes|yes|yes|no  
不同包子类|yes|yes|no|no  
不同包非子类|yes|no|no|no  


## 内部类  

### 概念与分类  

概念：如果一个事物的内部包含另一个事物，那么这就是一个类内部包含另一个类  
例如：身体和心脏的关系，又如：汽车和发动机的关系  

分类：  
1、成员内部类  
2、局部内部类(包含匿名内部类)  

### 定义格式
```  
修饰符 class 外部类名称{   
    修饰符 class 内部类名称{  
        //...  
        }  
        //...  
}
```

注意：内用外，随意访问；外用内，需要内部类对象  

### 成员内部类的使用  

1、间接方式：在外部类的方法中，使用内部类，然后main只是调用外部类的方法  
2、直接方法，公式：  
【外部类名称.内部类名称 对象名 = new 外部类名称().new 内部类名称();】  

```java
public class Body {//外部类
    public class Heart{//成员内部类
        //内部类的方法
        public void beat(){
            System.out.println("心脏跳动，蹦蹦蹦");
            System.out.println("我叫"+name);
        }
        //定义类的成员变量
        private String name;
        //外部类的方法
        public void methodbody(){
            new Heart().beat();
            System.out.println("外部类的方法");
        }

        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }
    }

}


public class Demo07Inner {
    public static void main(String[] args) {
        Body body = new Body();//外部类的对象
        //通过外部类的对象，调用外部类的方法，里面间接在使用内部类heart
        Body.Heart heart = new Body().new Heart();
        heart.beat();

    }
}
```

### 同名变量的访问  

如果出现了重名现象，那么格式是：外部类.this.外部类成员变量  

```java
public class Outer {
    int num = 10;

    public class Inner{
        int num = 20;
        public void method(){
            int num = 30;
            System.out.println(num);
            System.out.println(this.num);
            System.out.println(Outer.this.num);
        }
    }
}


public class Demo07Outer {
    public static void main(String[] args) {
        Outer.Inner inner = new Outer().new Inner();
        inner.method();
    }
}
```

### 局部内部类  

如果一个类是定义在一个方法内部，那么这就是一个局部内部类  
“局部”：只有当前所属的方法才能使用它，出了这个方法外面就不能用了。  

定义格式：  
```
修饰符  class  外部类名称{
    修饰符 返回值类型 外部类方法名称(){
        class 局部内部类{
            //...
        }
    }
}
```

小节一下类的权限修饰符：  
public > protected > (default) > private  
定义一个类的时候，权限修饰符规则：  
1、外部类：public / (default)  
2、成员内部类：public / protected / (default) / private  



