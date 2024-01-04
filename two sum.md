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
Dictionary <datatype, datatype> dictName = new Dictionary<datatype, datatype>();

dictName.add(arg1, arg2); // add to dictionary
dictName.ContainsKey(arg); // check if arg is in hashmap
```

```csharp
public class Solution {
    public int[] TwoSum(int[] nums, int target) {
		Dictionary<int, int> hashMap = new Dictionary<int, int>();
	
		for (i = 0; int < nums.length; i++) {
			for (j = i + 1; j < nums.length; j++) {
				compare = target - nums[i];
				
			}
		}
    }
}
```