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