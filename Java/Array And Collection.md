# 数组和集合

## 数组是什么

Java中数组是相同类型数据的有序集合。数组描述的是相同类型的若干个数据，按照一定的先后次序排列组合而成。其中，每一个数据称作一个元素，每个元素可以通过一个索引(下标)来访问它们。根据数组的维度，可以将其分为一维数组、二维数组和多维数组等。

## 数组的三个特点  

1.长度是确定的。数组一旦被创建，它的大小就是不可以改变的。  
2.其元素必须是相同类型，不允许出现混合类型。3. 数组类型可以是任何数据类型，包括基本类型和引用类型。

## 数组的声明

1.type[] arr_name;  
2.type arr_name[];

## 集合是什么

Java集合类存放在java.util包中，是一个用来存放对象的容器。集合类型主要有3种：set(集）、list(列表）和queue。集合存放的都是对象的引用，而非对象本身。所以我们称集合中的对象就是集合中对象的引用。  
1、List：里面存放的数据是有顺序的，可以存放重复的数据。  
2、Set：里面存放的数据是没有顺序的，不能存放重复的数据。  
3、queue：是一个队列，里面的数据是可以先进先出，可以存放重复的数据。

## List有三个实现类

ArrayList   LinkedList    Vector  
1 ArrayList底层是以数组实现的。  
2 LinkedList是双向链表实现，适合于经常进行增删操作，但是查询和修改效率没ArrayList、Vector快。  
3 Vector与ArrayList类似,也是数组实现，但是他是同步的,是线程安全的，不会有并发产生的问题，但是效率要低于ArrayList

## 数组和集合的区别

区别一：  
1、数组既可以存储基本数据类型，又可以存储引用数据类型，基本数据类型存储的是值，引用数据类型存储的是地址值  
2、集合只能存储引用数据类型（对象），如果存储基本数据类型时，会自动装箱变成相应的包装类。  
区别二：  
1、数组长度是固定的，不能自动增长  
2、集合的长度的是可变的，可以根据元素的增长而自动增长

## Array和List的区别

Array—是基于索引(index)的数据结构，它使用索引在数组中搜索和读取数据是很快的。Array获取数据的时间复杂度是O(1),但是要删除数据却是开销很大的，因为这需要重排数组中的所有数据。  
List—是一个有序的集合，可以包含重复的元素，提供了按索引访问的方式，它继承Collection。  
1、数组固定长度，一般是值的集合，需声明值类型；LIST是泛型集合，长度不固定，减少了拆箱装箱操作。当length不大时，两者无多大区别，较大时，使用数组更好。  
2、数组可读可写不能声明只读数组。集合类可以提供ReadOnly方法以只读方式使用集合。  
3、数组要有整数下标才能访问特定的元素，高效，然而很多时候这样的下标并不是很有用。LIST集合也是数据列表却不使用下标访问，要使用索引。
1、List和Array对索引元素的方式是不同的 ：Array是一段连续的存储结构。但是List则是不连续的存储结构, List的每个节点都有着一个Next属性，这个属性则记录着他的下一个节点的地址。  
2、 从空间扩展角度上来说：数组必须要在初始化时分配固定的大小，比如说int[] a=new int[3];如果我们仅仅写int[] a=new int[];编译器就会无情地给我们报错。但是List由于空间不必连续，所以无须指定初始大小。所以当不确定大小时，最好使用List 代替Array。
3、从操作角度上来看：当需要大量的查找操作时，最好使用Array。当需要进行频繁的插入，删除操作时，最好使用List代替Array。

## 打印数组

```java
public class Performance {
    int[] array = {1, 2, 3, 4, 5};

    {

        for (int i = 0; i < array.length; i++) {
            System.out.println(array[i]);
        }
    }
}
```

## 冒泡排序法

原理：  
1、比较相邻的元素。如果第一个比第二个大，就交换他们两个。  
2、对每一对相邻元素做同样的工作，从开始第一对到结尾的最后一对。在这一点，最后的元素应该会是最大的数。  
3、针对所有的元素重复以上的步骤，除了最后一个。  
4、持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

```java
public class BubbleSort {

    public static void main(String[] args) {
        int[] arr = {24, 69, 80, 57, 13};
        bubbleSort(arr);
        print(arr);
    }


    public static void bubbleSort(int[] arr) {
        for (int i = 0; i < arr.length - 1; i++) {                //外循环只需要比较arr.length-1次就可以了
            for (int j = 0; j < arr.length - 1 - i; j++) {        //-1为了防止索引越界,-i为了提高效率
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }


    public static void print(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            System.out.print(arr[i] + " ");
        }
    }

}
```

```java
public class QuickSorting {
        public static void main(String[] args) {
            // TODO Auto-generated method stub
            int[] intArray = {12,11,45,6,8,43,40,57,3,20};
            System.out.println("排序前的数组：");
            for(int i=0;i<intArray.length;i++) {
                System.out.print(" "+intArray[i]);//输出数组元素
                if((i+1)%5==0)//每5个元素一行
                    System.out.println();
            }
            System.out.println();
            int[] b = quickSort(intArray,0,intArray.length-1);//调用quickSort
            System.out.println("使用快速排序法后的数组：");
            for(int i=0;i<b.length;i++) {
                System.out.print(" "+b[i]);
                if ((i+1)%5==0) {//每5个元素一行
                    System.out.println();
                }
            }
        }

        private static int[] quickSort(int[] array, int left, int right) {//快速排序法
            // TODO Auto-generated method stub
            //如果开始点和结束点没有重叠的时候，也就是指针没有执行到结尾
            if (left<right-1) {
                int mid = getMiddle(array,left,right);//重新获取中间点
                quickSort(array,left,mid-1);
                quickSort(array,mid+1,right);
            }
            return array;

        }

        private static int getMiddle(int[] array, int left, int right) {
            // TODO Auto-generated method stub
            int temp;
            int mid = array[left];//把中心置于a[0]
            while(left < right) {
                while(left < right && array[right] >= mid)
                    right--;
                temp = array[right];//将比中心点小的数据移到左边
                array[right] = array[left];
                array[left] = temp;

                while(left < right && array[left] <= mid)
                    left++;
                temp = array[right];//将比中心点大的数据移到右边
                array[right] = array[left];
                array[left] = temp;
            }
            array[left] = mid;//中心移到正确位置
            return left;//返回中心点
        }



    }
```
