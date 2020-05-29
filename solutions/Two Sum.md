# Question

> Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.
>
> You may assume that each input would have ***exactly\*** one solution, and you may not use the *same* element twice.
>
> **Example:**
>
> ```
> Given nums = [2, 7, 11, 15], target = 9,
> 
> Because nums[0] + nums[1] = 2 + 7 = 9,
> return [0, 1].
> ```

# 算法

**暴力破解**

*想法*:获取到数组里面所有的两个值相加,如果相同就返回

```java
class Solution {
    
  	public int[] twoSum(int[] nums, int target) {
        for(int i = 0 ; i < nums.length;i++){
          for(int j = i + 1 ; j < nums.length ; j ++) {
            if(nums[j] == target - nums[i]){
              return new int[]{i,j};
            }
          }
        }
    		throw new IllegalArgumentExcepiton("no match");
    }
}
```

- 时间复杂度 O($n^2$)

    

**使用HashMap**

第一遍

```java
class Solution {
    
  	public int[] twoSum(int[] nums, int target) {
				HashMap<Integer,Integer> hashMap = new HashMap<>();
      	for(int i = 0; i < nums.length; i ++) {
        		hashMap.put(nums[i],i);
        }
      	for(int j = 0; j < nums.length; j ++){
          if(hashMap.containsKey(target-nums[j]) && hashMap.get(target-nums[j])!=j){
          	return new int[]{j,hashMap.get(target-nums[i])}
          }
        }
      	return new IllegalArgumentException("no match");
    }
}
```

其实这里我看discuss以后别人使用hashMap并不用先装在

因为是这样的

 array = [3,4] target = 7

7-3 和 7-4 是一样的

呜呼,这一点意识到了就不用想把数据第一次全装到hashMap了 我可以遍历的时候再装进去

```java
class Solution {
    
  	public int[] twoSum(int[] nums, int target) {
				HashMap<Integer,Integer> hashMap = new HashMap<>();
      	for(int i = 0; i < nums.length ; i ++){
          		if(hashMap.containsKey(target-nums[i])){
                		return new int[]{i,hashMap.get(target-nums[i])};
              }
          		hashMap.put(nums[i],i);
        }
    		throw new IllegalArgumentException("no match");
    }
  	
}
```



