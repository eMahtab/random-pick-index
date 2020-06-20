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

# Implementation 2 : No Extra Space
```java
class Solution {
    int[] nums;
    Random random;
    
    public Solution(int[] nums) {
       this.nums =  nums;
       random = new Random(); 
    }
    
    public int pick(int target) {
        int count = 0;
        int index = 0;
        
        for (int i = 0; i < nums.length; i++) {
            if(nums[i] == target) {
                count++;
                // This if changes the probability of an index i to be selected
                if(random.nextInt(count) == 0) { 
                    index = i;
                }
            }
        }
        return index;
    }
}

/**
 * Your Solution object will be instantiated and called as such:
 * Solution obj = new Solution(nums);
 * int param_1 = obj.pick(target);
 */
```
