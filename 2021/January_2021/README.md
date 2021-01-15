## 1/14/2021
Two Sum problem from leetcode (https://leetcode.com/problems/two-sum)
Problem: Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.
You may assume that each input would have exactly one solution, and you may not use the same element twice.
You can return the answer in any order.
Efficient Solution: Using hashmaps will minimize the time and space complexity
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int[] result = new int[2];
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        for(int i = 0; i < nums.length; i++){
            int difference = target - nums[i];
            if(map.containsKey(difference)){
                result[0] = i;
                result[1] = map.get(difference);
                return result;
            }
            map.put(nums[i], i);
        }
        
        return result;
    }
}
```
## 1/15/2021
Now I understand how to setup an ssh connection for github and my host machine so I won't have to login every time I push any updates
```
ssh-keygen -t rsa -b 4096 -C "<email>"
```
