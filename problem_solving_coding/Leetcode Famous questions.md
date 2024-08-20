1. **Two Sum**: Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

```js
// Example 1
Input: (nums = [2, 7, 11, 15]), (target = 9);
Output: [0, 1];
```

```js
// Example 2
Input: (nums = [3, 2, 4]), (target = 6);
Output: [1, 2];
```

```js
// Example 3
Input: (nums = [3, 3]), (target = 6);
Output: [0, 1];
```

<details>
<summary>View Answer</summary>

</details>

---

**4. Number of Good Pairs**

```js
Example 1:
Input: nums = [1,2,3,1,1,3]
Output: 4
Explanation: There are 4 good pairs (0,3), (0,4), (3,4), (2,5) 0-indexed.

Example 2:
Input: nums = [1,1,1,1]
Output: 6
Explanation: Each pair in the array are good.

Example 3:
Input: nums = [1,2,3]
Output: 0
```

---

**5. Count the Number of Consistent Strings**

```js
Example 1:
Input: allowed = "ab", words = ["ad","bd","aaab","baa","badab"]

Output: 2
Explanation: Strings "aaab" and "baa" are consistent since they only contain characters 'a' and 'b'.

Example 2:
Input: allowed = "abc", words = ["a","b","c","ab","ac","bc","abc"]
Output: 7
Explanation: All strings are consistent.

Example 3:
Input: allowed = "cad", words = ["cc","acd","b","ba","bac","bad","ac","d"]
Output: 4
Explanation: Strings "cc", "acd", "ac", and "d" are consistent.
```

---

**9. Longest Consecutive Sequence- Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.**

```js
Example 1:
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.

Example 2:
Input: nums = [0,3,7,2,5,8,4,6,0,1]
Output: 9
Explanation: The longest consecutive elements sequence is [0, 1, 2, 3, 4, 5, 6, 7, 8]. Therefore its length is 9.
```

---

**10.First Unique Character in a String - Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1.**

```js
Example 1:
Input: s = "leetcode"
Output: 0

Example 2:
Input: s = "loveleetcode"
Output: 2

Example 3:
Input: s = "aabb"
Output: -1
```

---

**11.Find Common Characters - Given a string array words, return an array of all characters that show up in all strings within the words (including duplicates). You may return the answer in any order.**

```js
Example 1:
Input: words = ["bella","label","roller"]
Output: ["e","l","l"]

Example 2:
Input: words = ["cool","lock","cook"]
Output: ["c","o"]
```

---

**12. Sort Characters By Frequency - sort it in decreasing order based on the frequency of the characters. The frequency of a character is the number of times it appears in the string. Return the sorted string. If there are multiple answers, return any of them.**

```js
Example 1:
Input: s = "tree"
Output: "eert"
Explanation: 'e' appears twice while 'r' and 't' both appear once.
So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.

Example 2:
Input: s = "cccaaa"
Output: "aaaccc"
Explanation: Both 'c' and 'a' appear three times, so both "cccaaa" and "aaaccc" are valid answers.
Note that "cacaca" is incorrect, as the same characters must be together.

Example 3:
Input: s = "Aabb"
Output: "bbAa"
Explanation: "bbaA" is also a valid answer, but "Aabb" is incorrect.
Note that 'A' and 'a' are treated as two different characters.
```

---
