# Leecode

## 75颜色分类

给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列  
此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。  
注意:  
不能使用代码库中的排序函数来解决这道题。  
示例:  
输入: [2,0,2,1,1,0]  
输出: [0,0,1,1,2,2]

```java
class Solution {
    public void sortColors(int[] nums){
        boolean isSorted=false;
        for (int i = 0; i < nums.length- 1; i++) {
            System.out.println(isSorted);
            if (isSorted) return;
            isSorted = true;
            for (int j = 0; j <nums.length - 1 - i; j++) {
                if (nums[j] > nums[j + 1]) {
                    int temp = nums[j];
                    nums[j] = nums[j + 1];
                    nums[j + 1] = temp;
                    isSorted = false;
                    System.out.println("i" + i + Arrays.toString(nums));
                }
            }
        }
        }
}
```

```java
import java.util.Arrays;

public class QuickSorting {
    public void sortColors(int[] nums) {
        quickSort(nums, 0, nums.length - 1);
    }

    public void quickSort(int[] nums, int left, int right) {
        if (left < right) {
            int middle = partition(nums, left, right);
            quickSort(nums, left, middle - 1);
            quickSort(nums, middle + 1, right);
        }

    }

    public int partition(int[] nums, int left, int right) {
        int pivot = nums[right];
        // System.out.println(pivot);
        int i = left - 1;
        int j = left;
        while (i < j && j < right) {
            if (nums[j] <= pivot) {
                i = i + 1;
                int temp = nums[i];
                nums[i] = nums[j];
                nums[j] = temp;
            }
            j++;
        }
        System.out.println(Arrays.toString(nums));
        //System.out.println(nums[i + 1] + " " + pivot);
        int tmp = nums[i + 1];
        nums[i + 1] = pivot;
        nums[right] = tmp;
        //System.out.println(Arrays.toString(nums));
        return i + 1;
    }

    public static void main(String[] args) {
        int nums[] = new int[]{12, 11, 45, 6, 8, 43, 40, 57, 3, 20};
        QuickSorting quickSorting = new QuickSorting();
        quickSorting.sortColors(nums);
        System.out.println(nums);
}
    }
```
