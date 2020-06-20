# Random pick index
## https://leetcode.com/problems/random-pick-index



# Implementation 1 : Naive
```java
class Solution {
    Map<Integer,List<Integer>> map;
    Random random; 
    
    public Solution(int[] nums) {
        map = new HashMap<Integer, List<Integer>>();
        random = new Random();
        for(int i = 0; i < nums.length; i++) {
            map.putIfAbsent(nums[i], new ArrayList<Integer>());
            map.get(nums[i]).add(i);
        }
    }
    
    public int pick(int target) {
        int occurances = map.get(target).size();  
        int randomIndex = random.nextInt(occurances);
        return map.get(target).get(randomIndex);
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * int param_1 = obj.pick(target);
 */
```
