# Question

> Given an array `nums` of *n* integers, are there elements *a*, *b*, *c* in `nums` such that *a* + *b* + *c* = 0? Find all unique triplets in the array which gives the sum of zero.
>
> **Note:**
>
> The solution set must not contain duplicate triplets. 这句去重才是需要考虑很多的问题
>
> **Example:**
>
> ```
> Given array nums = [-1, 0, 1, 2, -1, -4],
> 
> A solution set is:
> [
>   [-1, 0, 1],
>   [-1, -1, 2]
> ]
> ```

# 算法

定义三个角标来移动角标判断

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        // -4,-3,1,3 左边重复元素
        // i  mid  right
        // -1,0,0,0,0,0,0,1 中间有重复元素
        // 0 ,0,0
        // -1,0,1,1 (-1,0,1)
        // Solution1: 
        Arrays.sort(nums);
        ArrayList<List<Integer>> lists = new ArrayList<>();
        for(int i = 0 ;i < nums.length -2 ; i++){
         int mid = i + 1,right = nums.length -1;
            if(i == 0 || nums[i] != nums[i-1]){
                while(mid < right ){
                    int nowValue = nums[i] + nums[mid] + nums[right];
                    // nowValue 
                    if(nowValue < 0) {
                       mid ++; 
                    }else if(nowValue > 0){
                        right --;
                    }else{
                        // 中间包括了 中间有相同元素 右边有相同元素 
                        lists.add(Arrays.asList(nums[i],nums[mid],nums[right]));
                        while(mid <right &&  nums[mid]==nums[mid+1]) mid++;
                        while(mid <right && nums[right] == nums[right-1]) right --;
                        mid++;
                        right--;
                    } 
                }   
            }
        }
        return lists;
    }
                                  
}
```





