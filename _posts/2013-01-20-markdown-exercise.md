---

layout: post
title: Move Zeroes
tags: leetcode

---

#### Problem: Given an array nums, write a function to move all 0’s to the end of it while maintaining the relative order of the non-zero elements. For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

### 双指针压缩法
>**复杂度：** 时间 O(N) 空间 O(1)
>**思路：** 实际上就是将所有的非0数向前尽可能的压缩，最后把没压缩的那部分全置0就行了。比如103040，先压缩成134，剩余的3为全置为0。过程中需要一个指针记录压缩到的位置。
>**代码：**
>```
public class Solution {
    public void moveZeroes(int[] nums) {
      while(nums==null||nums.length==0) return;
      int j=0;
      for(int i=0;i<nums.length;i++){
        if(nums[i]!=0){
        nums[j]=nums[i];
        j++;
        }
      }
    for(;j<nums.length;j++){
    nums[j]=0;
    }
  }
}
```

### 思维扩散
- 若改成把数组中所有0放在前面而不是后面呢？nums=[0, 0, 1, 3, 12]

  同样的解题思路，但是是从后向前遍历，将非0数字压缩到后面。

 > **代码修改如下：**
 >```
 public class Solution {
    public void moveZeroes(int[] nums) {
        while(nums==null||nums.length==0)
        return;
        int j=nums.length-1;
        for(int i=nums.length-1;i>=0;i--){
            if(nums[i]!=0){
                nums[j]=nums[i];
                j--;
            }
        }
        for(;j>=0;j--){
            nums[j]=0;
        }
    }
 }
```
- 同类问题为把相同的数字（元素）放在句尾或句首。
  同样的解题思路，将0替换为相同的元素。
