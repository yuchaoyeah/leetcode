# Question

> Given an array `nums` of *n* integers and an integer `target`, find three integers in `nums` such that the sum is closest to `target`. Return the sum of the three integers. You may assume that each input would have exactly one solution.
>
>  
>
> **Example 1:**
>
> ```
> Input: nums = [-1,2,1,-4], target = 1
> Output: 2
> Explanation: The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).
> ```
>
>  
>
> **Constraints:**
>
> - `3 <= nums.length <= 10^3`
> - `-10^3 <= nums[i] <= 10^3`
> - `-10^4 <= target <= 10^4`

# 算法 

与Three Sum类似

```java
class Solution {
    public int threeSumClosest(int[] nums, int target) {
        Arrays.sort(nums);
        int minValue = nums[0] + nums[1] + nums[2];
        for(int i = 0 ; i< nums.length -2 ; i ++){
            int mid = i +1 , right = nums.length -1;
            if(i == 0 || nums[i-1]!= nums[i]){
                while(mid<right){
                    int nowValue = nums[i] + nums[mid] + nums[right];
                    if(nowValue < target){
                        while(mid < right && nums[mid] == nums[mid+1]) mid++;
                        mid++;
                    }else if (nowValue > target){
                        while(mid < right && nums[right] == nums[right-1]) right--;
                        right--;
                    }else{
                        return nowValue;
                    }                  //4       3
                    minValue = Math.abs(target - nowValue) > Math.abs(target -minValue) ? minValue : nowValue;
                }
            }

        }
        return minValue;
    }
}
```

