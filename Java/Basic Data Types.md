# java数据类型

1、byte（字节型）：定义整型数据（范围-128到127）占一个字节  
2、short（短整型）：定义整形数据（范围-32768到32768)占两个字节  
3、int（整型）：定义整型数据（范围-2^31到2^31-1）占四个字节  
4、long（长整型）：定义整形数据（范围-922337203685477808到922337203685477808）占八个字节  
5、float（单精度浮点型）：定义浮点数类型 占四个字节  
6、double（双精度浮点型）：定义浮点数类型 站八个字节  
7、char（字符型）：定义字符型 占两个字节  
8、Boolean（布尔型）：定义布尔值 占一个字节

**为什么int的值是2^31?**  
32个格子中放满0或1的方法有2的32次方种。  
所以有两种可能：  
最小的情况是：000000000000000000000000000000000  
最大的情况是：1111111111 1111111111 1111111111 11  
因此，可以有两种推算方法：  
1、将二进制最大的数字（32个1）转换成10进制，即 4294967296  
2、有2的32次方种算法，那么依照10进制最大的数就是2的32次方。即4294967296.  
不过，这样的计算的是无符号。即正数。可是java中int有正负之分。所以32个格子中占用一个格子标识正负。所以仅仅能用31个格子来标识数值：所以java中的int的取值范围：2的31次方：+/- 2147483648)

## java的数据类型和包装类型的对应关系

byte → Byte

short → Short

int → Integer

long → Long

float → Float

double → Double

char → Character

boolean→ Boolean

## 基本数据类型与包装类的相互交换

由基本数据类型向对应的包装类转换称为装箱，例如把int包装成integer类的对象

由包装类相对应的基本数据类型转换称为拆箱，例如把integer类的对象重新简化为int

## 拆箱和装箱

自动拆箱：对象转换成基本数值

自动装箱：基本数值转换成对象

### int和integer装箱用的方法

1、构造方法：Integer(int value）  
构造一个新分配的 Integer对象，该对象表示指定的 int值。  
2、静态方法：static Integer valueOf(int i)  
返回一个 Integer指定的 int值的 Integer实例。

### int和integer拆箱用的方法

1、成员方法  
int intvalue()以int类型返回Integer的值。

```java
public class Test {
    public static void main(String[] args) {
        int a = 3; //基本数据类型
        Integer it = new Integer(a);//基本数据类型转换成封装类型
        Integer it1 = a;//装箱     基本数据类型通过=自动转换成类类型
        int a1 = it.intValue(); //封装类型转换成基本数据类型
        int a2 = it1; //拆箱      通过=自动转换成int型
    }
}
```

### 在Integer中valueOf和intValue的方法

```java
public boolean equals(Object obj) {
        if (obj instanceof Integer) {
            return value == ((Integer)obj).intValue();
        }
        return false;
    }
```

```java
public static Integer valueOf(int i) {
        if (i >= IntegerCache.low && i <= IntegerCache.high)
            return IntegerCache.cache[i + (-IntegerCache.low)];
        return new Integer(i);
    }
```

## 缓存池

Integer 缓存池的大小默认为 -128~127

```java
private static class IntegerCache {
        static final int low = -128;
        static final int high;
        static final Integer cache[];

        static {
            // high value may be configured by property
            int h = 127;
            String integerCacheHighPropValue =
                sun.misc.VM.getSavedProperty("java.lang.Integer.IntegerCache.high");
            if (integerCacheHighPropValue != null) {
                try {
                    int i = parseInt(integerCacheHighPropValue);
                    i = Math.max(i, 127);
                    // Maximum array size is Integer.MAX_VALUE
                    h = Math.min(i, Integer.MAX_VALUE - (-low) -1);
                } catch( NumberFormatException nfe) {
                    // If the property cannot be parsed into an int, ignore it.
                }
            }
            high = h;

            cache = new Integer[(high - low) + 1];
            int j = low;
            for(int k = 0; k < cache.length; k++)
                cache[k] = new Integer(j++);

            // range [-128, 127] must be interned (JLS7 5.1.7)
            assert IntegerCache.high >= 127;
        }

        private IntegerCache() {}
    }
```
