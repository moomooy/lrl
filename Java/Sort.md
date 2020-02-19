# 排序

## 冒泡排序法

原理：  
1、比较相邻的元素。如果第一个比第二个大，就交换他们两个。  
2、对每一对相邻元素做同样的工作，从开始第一对到结尾的最后一对。在这一点，最后的元素应该会是最大的数。  
3、针对所有的元素重复以上的步骤，除了最后一个。
4、持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

例子：  
24, 69, 80, 57, 13  
第一趟后：24，69，57，13，80  
第二趟后：24，57，13，69，80  
第三趟后：24，13，57，69，80  
第四趟后：13，24，57，69，80

```java
public class BubbleSort {

    public static void main(String[] args) {
        int[] arr = {1,2,3,4,5,6};
        bubbleSort(arr);
        print(arr);
    }


    public static void bubbleSort(int[] arr) {
        int count=1;
        boolean isSorted=false;
        for (int i = 0; i < arr.length - 1; i++) {//外循环只需要比较arr.length-1次就可以了
            if(isSorted)return;
            for (int j = 0; j < arr.length - 1 - i; j++) {//-1为了防止索引越界,-i为了提高效率
                System.out.println("第" + count + "次循环");
                count++;
                isSorted = true;
                if (arr[j] > arr[j + 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    isSorted = false;
                    System.out.println("第" + count + "次打印" + Arrays.toString(arr));
                    count++;
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

## 快速排序法

分治算法：分治算法的基本思想是将一个规模为N的问题分解为K个规模较小的子问题，这些子问题相互独立且与原问题性质相同。求出子问题的解，就可得到原问题的解。即一种分目标完成程序算法，简单问题可用二分法完成。

1、选定Pivot中心轴  
2、将大于Pivot的数字放在Pivot的右边  
3、将小于Pivot的数字放在Pivot的左边  
4、分别对左右子序重复前三步操作  
  
例子：12，11，45，6，8，43，40，57，3，20  
以12为Pivot中心轴  
第一趟后：11，3，6，8，12，43，40，57，45，20  
第二趟后：3，6，8，11，12，40，20，43，45，57  
第三趟后：3，6，8，11，12，20，40，43，45，57  
第四趟后：3，6，8，11，12，20，40，43，45，57  

```java
public class QuickSorting {
    public static int[] qsort(int arr[],int start,int end) {
        int pivot = arr[start];
        int i = start;
        int j = end;
        int count=1;
        while (i<j) {
            while ((i<j)&&(arr[j]>pivot)) {
                j--;
            }
            while ((i<j)&&(arr[i]<pivot)) {
                i++;
            }
            if ((arr[i]==arr[j])&&(i<j)) {
                i++;
            } else {
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
            System.out.println("第" + count + "次打印" + Arrays.toString(arr));
            count++;
        }
        if (i-1>start) arr=qsort(arr,start,i-1);
        if (j+1<end) arr=qsort(arr,j+1,end);
        return (arr);
    }

    public static void main(String[] args) {
        int arr[] = new int[]{12,11,45,6,8,43,40,57,3,20 };
        int len = arr.length-1;
        arr=qsort(arr,0,len);
        for (int i:arr) {
            System.out.print(i+"\t");
        }
    }
    }
```

## 归并排序

归并排序:  
1、申请空间，使其大小为两个已经排序序列之和，该空间用来存放合并后的序列  
2、设定两个指针，最初位置分别为两个已经排序序列的起始位置  
3、比较两个指针所指向的元素，选择相对小的元素放入到合并空间，并移动指针到下一位置  
重复步骤3直到某一指针超出序列尾  
将另一序列剩下的所有元素直接复制到合并序列尾

## 例子

 设有数列：{9, 8, 7, 6, 5, 4, 3, 2, 10 }  
 初始状态： 9, 8, 7, 6, 5, 4, 3, 2, 10)  
 第一次归并后：{8，9}，{6，7}，{4，5}，{2，3}，{10}比较次数4次  
 第二次归并后：{6，7，8，9}，{2，3，4，5}，{10}比较次数2次  
 第三次归并后：{2，3，4，5，6，7，8，9}，{10}比较一次  
 第四次归并后：{2，3，4，5，6，7，8，9，10}

 ```java
 public class MergeSort {
        public static int[] mergeSort(int[] nums, int l, int h) {
            if (l == h)
                return new int[] { nums[l] };

            int count=1;
            int mid = l + (h - l) / 2;
            int[] leftArr = mergeSort(nums, l, mid); //左有序数组
            int[] rightArr = mergeSort(nums, mid + 1, h); //右有序数组
            int[] newNum = new int[leftArr.length + rightArr.length]; //新有序数组

            int m = 0, i = 0, j = 0;
            while (i < leftArr.length && j < rightArr.length) {
                newNum[m++] = leftArr[i] < rightArr[j] ? leftArr[i++] : rightArr[j++];
            }
            while (i < leftArr.length)
                newNum[m++] = leftArr[i++];
            while (j < rightArr.length)
                newNum[m++] = rightArr[j++];
            System.out.println("第" + count + "次打印" + Arrays.toString(newNum));
            count++;
            return newNum;
        }
        public static void main(String[] args) {
            int[] nums = new int[] { 9, 8, 7, 6, 5, 4, 3, 2, 10 };
            int[] newNums = mergeSort(nums, 0, nums.length - 1);
            for (int x : newNums) {
                System.out.println(x);
            }
        }
    }
```
