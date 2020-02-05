# java

## 类 ：在Java语言里，最基本的单位是类（class），类=成员变量+方法                                                        类是一组相关属性和行为的集合，类一般泛指莫一件事                                                                         定义类的格式是  类的修饰词 class 类名{ 类体，成员变量和方法组成}

## 类变量有成员变量和成员变量：写在类里面，方法体的外面，声明时可以不进行初始化值，可以被本类或其他类的方法局部变量：写在方法体的里面，声明时可以不初始化，但是在使用前一定要初始化，只能在声明局部变量的方法内进行调用

## 方法 第一步，访问修饰符 第二步，关键词。关键词主要有static和abstract两个关键词。第三步，返回值有否？如果有返回值就是有返回值方法。有返回值，则写具体返回类型，比如string int 等，这就是java强类型的一个表现。第四步。方法的名称。为了见名知意，也就是可以自定义。第五步，参数列表。现实是多姿多彩的，需要很多的形容词来修饰，而在编程中就需要很多的变量来修饰 第六步。方法体。主要的区别就在于有无。也就是有具体的方法体以及没有方法体。甚至都可以没有大括号。小括号就能组成一个方法。 最简单的方法就是方法名（）

## 从1加100  package lrl;             public class llll                 public static void main (String[] args) {    int s=0;for(int i=1;i<100;i++) {}s=s+i;System.out.println("s="+s);}}

## 对象有三个特征：继承，封装，多肽 1、继承   实现：extends 原理：子类可以继承父类的所有属性和方法   例如这题                   public class Cleanser {                                                                                              private String s=new String("Cleanser");                                                                             public void append(String a) { s+=a;}                                                                                public void dilute() {append("dilute()");}                                                                           public void apply() {append("apply()");}                                                                             public void scrub() {append("scrub()");}                                                                             public void print() {System.out.println(s);}                                                                         public static void main(String[] args) {                                                                             Cleanser x=new Cleanser();                                                                                           x.dilute();x.apply();x.scrub();x.print();}}                                                                          public class Detergent extends Cleanser {                                                                            // Change a method:                                                                                                  public void scrub() {                                                                                                append(" Detergent. scrub()");                                                                                       super.scrub(); // Call base-class version}                                                                           // Add methods to the interface:                                                                                       public void foam() { append(" foam()"); }                                                                              // Test the new class:                                                                                            public static void main(String[] args) {                                                                             Detergent x = new Detergent();                                                                                       x.dilute(); x.apply(); x.scrub(); x.foam();x.print();                                                                 System. out. println("Testing base class:");                                                                        Cleanser.main(args);}} ///:~                                                                                         在这题中Detergent是洗涤剂 cleanser是清洁剂洗脸的 append是增加，附加  dilute是稀释冲淡  apply是涂 scrub是擦 foam是泡沫  子类继承了父类的x.dilute();x.apply();x.scrub();x.print();这些方法，比较公用的方法一般放在父类里

## java的八大基本数据类型：1、byte（字节型）：定义整型数据（范围-128~127）占一个字节                                                              2、short（短整型）：定义整形数据（范围-32768~32768)占两个字节                                                          3、int（整型）：定义整型数据（范围-2147483648~2147483648）占四个字节                                                   4、long（长整型）：定义整形数据（范围-922337203685477808~922337203685477808）占八个字节                                5、float（单精度浮点型）：定义浮点数类型 占四个字节                                                                    6、double（双精度浮点型）：定义浮点数类型 站八个字节                                                                   7、char（字符型）：定义字符型 占两个字节                                                                               8、Boolean（布尔型）：定义布尔值 占一个字节