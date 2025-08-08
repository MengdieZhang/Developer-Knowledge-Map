Leetcode:34, 2529, 2300. 2563, 275, 875, 2187, 2439, 2517
### 2439 Minmize Maximum of Array:
Using prefix to solve this problem.  In the description, "
In one operation, you must:

Choose an integer i such that 1 <= i < n and nums[i] > 0.
Decrease nums[i] by 1.
Increase nums[i - 1] by 1.", which means we just can move piles from right to left. to find the ceil of average of current sum is the minimize maximum. The nums[0] cannot be decreased, so the result should be equal or greater than nums[0];


```
class Solution {
    public int minimizeArrayValue(int[] nums) {
        long sum = nums[0];
        int res = nums[0];
        for (int i = 1; i < nums.length; i++) {
            sum += nums[i];
            int avg = (int) Math.ceil((double) sum / (i + 1));
            res = Math.max(res, avg);
        }
        return res;
    }
}
```