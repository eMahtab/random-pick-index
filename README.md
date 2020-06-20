# Random pick index
## https://leetcode.com/problems/random-pick-index

Given an array of integers with possible duplicates, randomly output the index of a given target number. You can assume that the given target number must exist in the array.

**Note:**

The array size can be very large. Solution that uses too much extra space will not pass the judge.
```
Example:

int[] nums = new int[] {1,2,3,3,3};
Solution solution = new Solution(nums);

// pick(3) should return either index 2, 3, or 4 randomly. Each index should have equal probability of returning.
solution.pick(3);

// pick(1) should return 0. Since in the array only nums[0] is equal to 1.
solution.pick(1);
```

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

**Tip :**
To better understand the second implementation, run through some examples. 
e.g. int[] nums = [1, 2, 3] , target = 3
e.g. int[] nums = [1, 2, 3, 3] , target = 3
e.g. int[] nums = [1, 2, 3, 3, 3] , target = 3

# References :
https://www.youtube.com/watch?v=Tt1j0mVzHdg
