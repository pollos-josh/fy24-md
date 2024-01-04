First solution I tried is a typical `for` loop.
```csharp
public class Solution {
    public int[] TwoSum(int[] nums, int target) {
       int i;
       int j = i + 1;
       for (i < nums.length; i++;) {
           for (j < num; j++;) {
			   if (nums[i] + nums[j] == target)
			   return new int[] {i, j};
                }
           }
       }
       return new int[2];
    }
}
```


But looking for a more efficient algorithm in `O(n)` linear time, hash maps are still required.
*ref: [[two sum python]]*

`Dictionary` syntax
```csharp
Dictionary <datatype, datatype> dictName = new 
```