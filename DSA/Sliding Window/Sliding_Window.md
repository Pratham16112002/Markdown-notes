## Sliding window

Technique to reduce the use of nested loops and replace it with a single loop.<br>

Used when we see the following terms <br>
`Array, Strng Sub Array/String, Largest Sum, Maximum & Minimum Sum`

### Longest Substring with at least k repeating characters

<span style='color:Tomato'>Recursion + Sliding Window</span>

I/P : `s = "aaabb", k = 3`<br>
O/P : `3`

**Thinking** :<br>
The characters with a frequency less than k will not appear in the string.<br>
These un-even frequencies can be considered as break points in the given string.<br>
We need to generate the maximum string from those break points which satisfies the condition.<br>

**Approach** : <br>

1. n &larr; len(s).
2. if n == 0 | n < k : return 0.
3. if k == 1 | return n. <span style='color:Orange'>Entire string is valid then.</span>
4. len &larr; 0.
5. make frequency map for string s
6. while len < n & map[len] >= k.
7. len++.
8. if len >= n + 1 : return l.
9. l1 &larr; recursive(s.substr(0,l),k).
10. l2 &larr; recursive(s.sbustr(l),k).
11. return max(l1,l2)

Time Complexity : $O(n^2)$.

### Find All anagrams

<span style='color:SlateBlue'>Two Pointer + Hashing</span>

I/P : `s = "cbaebabacd", p = "abc"`<br>
O/P : `[0,6]`

**Thinking** : <br>

- We can create a hash of the given p string.
- Will will creata another hash for a window of size equal to the size of p string.
- Move the window while adding and remove characters form the hash and comparing it with the pre computed hash.

**Approach** : <br>

1. frequency_map &larr; p.
2. p.len > s.len return s.len.
3. left = 0 , right = 0.
4. for 0 to windowSize.
5. mp[s[right++]]++.
6. while right < n :
7. if mp === p.map ans.add(left).
8. right++.
9. if right != len(s).
10. mp[s[right]]++.
11. mp[s[left]] &larr; mp[s[left]]+1.
12. left++;

Time complexity : $ O(n) $.

### Remove Duplicates

_Note &rarr; given array will be sorted_.
<span style='color:Tomato'>Two Pointer</span><br>
Input : `nums = [0,0,1,1,1,2,2,3,3,4]`
Output : `5, nums = [0,1,2,3,4,_,_,_,_,_]`

**Note** :
In question we are given not to take any auxiliary  array.

**Brute Approach** :

- Using extra space and storing unique element from the given array.
- Require extra space of $ O(n) $.

**Optimal Approach** :

1. left &larr; 1 , right &larr; 1. (Since first element will not change its place)
2. n &larr; array.size().
3. while right < n
4. if nums[right-1] == nums[right]
5. nums[left] = nums[right]
6. left++
7. endIf
8. right++
9. endWhile

Time complexity : $ O(n) $ , Complexity : $O(1) $.
