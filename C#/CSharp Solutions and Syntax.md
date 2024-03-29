[[Bootcamp Notes]]
---
# C# Solutions and Syntax
## Two Sum

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

**doesn't work**

```csharp
public class Solution {
    public int[] TwoSum(int[] nums, int target) {
		Dictionary<int, int> hashMap = new Dictionary<int, int>();
	
		for (i = 0; int < nums.length; i++) {
			for (j = i + 1; j < nums.length; j++) {
				int compare = target - nums[i];
				if (hashMap.ContainsKey(compare)) {
					return new int[] {hashMap[compare], i};
				}
				if (!hashMap.ContainsKey(nums[i])) {
					hashMap[nums[i]] = 1
				}
			}
		}
		return new int[] {2};
    }
}
```

## Valid Anagram

Anagram checks involve some kind of array sorting. Push both sorted strings into arrays then compare them.

| a   | n   | a   | g   | r   | a   | m   |
| --- | --- | --- | --- | --- | --- | --- |
| m   | a    | r    | g    | a    | n    | a    |

```csharp
char[] sArray = s.ToCharArray();
char[] tArray = t.ToCharArray();

Array.Sort(sArray);
Array.Sort(tArray);

if (sArray.Length != tArray.Length) {
	return false;
}

for (int i = 0; i < sArray.Length; i++) {
	if (sArray[i] != tArray[i]) {
		return false;
	}
}
```

## Group Anagrams

Looking at my previous solution in python (ref: [[group anagrams]]), the most efficient solution is a `hashMap` then a `for` loop to group them together.

```csharp
public class Solution {
	public IList<IList<string>> GroupAnagrams(string[] strs) {
		Hashtable hashTable = new Hashtable();
		for (int i = 0; i < strs.Length; i++) {
			sortedWord = SortString(strs[i]);
			hashTable[sortedWord].Add(i);
		}
		
	}
	public static void SortString(string input) {
		char[] characters = input.ToArray();
		Array.Sort(characters);
		return new string(characters);
	}
}
```

Corrected code:

```csharp
public class Solution {
    public IList<IList<string>> GroupAnagrams(string[] strs) {
        Hashtable hashTable = new Hashtable();
        foreach (string str in strs) {
            string sortedWord = SortString(str);
            if (!hashTable.ContainsKey(sortedWord)) {
                hashTable[sortedWord] = new List<string>();
            }
            ((List<string>)hashTable[sortedWord]).Add(str);
        }
        return new List<IList<string>>(hashTable.Values.Cast<IList<string>>());
 }
    public static string SortString(string input) {
        char[] characters = input.ToCharArray();
        Array.Sort(characters);
        return new string(characters);
    }
}
```

However, a more modern approach is by using `dictionary`:

```csharp
public class Solution {
	public IList<IList<string>> GroupAnagrams(string[] strs) {
		public Dictionary<string, List<string>> dictionary = new Dictionary<string, List<string>>();
		foreach (string str in strs) {
			string sortedWord = SortString(str);

			if (!dictionary.ContainsKey(sortedWord)) {
				dictionary[sortedWord] = new List<string>(); // if sorted word is not in dictionary, make new list
			}
			
			dictionary[sortedWord].Add(str); // add current string to anagram group
		}
		return new List<IList<string>>(dictionary.Values); // return anagram groups as list
	}

	public static string SortString(string input) {
        char[] characters = input.ToCharArray();
        Array.Sort(characters);
        return new string(characters);
    }
}
```
