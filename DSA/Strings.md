### Sort Characters by frequency

You have given a string sort it in descending order based on the frequency return the string .

I/P : **`abcAbc`**

O/P : **`bbccAa`**

- Create a map
- Store all the characters along with their frequency .
- Create a vector of pair

> because we cannot sort a map using inbuilt sort method .

- Sort the vector in descending order of frequency .
- Add the characters according to the frequency of chars .

```cpp
unordered_map<char,int> mp;
	for(int i = 0 ; i<n ; i++){
		mp[s[i]]++;
	}
	vector<pair<char,int>> sortedVector(mp.begin(),mp.end());

	sort(sortedVector.begin() , sortedVector.end() , [](const pair<char, int>& a, const pair<char, int>& b) {
             return a.second > b.second;
         });
	string ans = "";
	for(auto it : sortedVector){
		for(int i = 0 ; i<it.second ; i++){
			ans+=it.first;
		}
	}
	return ans;
```

Time Complexity :

$$
O \left( n  \right)  +O \left( m  \right)  +O \left( m \log\left( m  \right)    \right)   
$$

Space Complexity :

$$
O \left( n+m  \right)   
$$

## Longest Palindromic substring

I/P : **`abccbc`**

O/P : **`bccb`**

There are multiple ways to solve this problem .

1.  **Brute force** : Generating all the substring and checking each one of them for palindrome and get the longest one .
    Time Complexity would be cubic
    $$
        O \left( n \cdot  n \cdot  n  \right)   
    $$
2.  **Dynamic Programming** : The palindrome is a string which is common in normal string as well as the reverse of the same string .
    We will find the Longest one with the longest common subsequence using dynamic programming algorithm .
    **Time complexity :**

        $$
        O \left( n \cdot  n  \right)   
        $$

3.  **Optimal Method** :

- Iterate over the string .
- Assume two pointers left and right assigned to current index .
  move them until we find the palindrome .
  get the maximum Length while traversing .
- Assume two pointers left assigned to current index and left assigned to current index + 1
  move them until we find the palindrome get the maximum Length while traversing .
- Return the final substring .

```cpp
int start = 0 ; //  position of string
        int maxLen = 1 ;  // length of the substring
        if( s.size() == 1){
            return s;
        }
        int left , right;
        for(int i = 0 ; i<s.size() ;i++){
            // checking for even length palidromes
            left = i ;
            right = i + 1;
            while(left >= 0 && right < s.size() &&  s[left] == s[right]){
                if(right - left + 1 > maxLen){
                    start = left;
                    maxLen = right - left + 1;
                }
                left--;
                right++;
            }
            // checking for odd length palindrome
            left = right = i ;
            while(left >= 0 && right < s.size() && s[left] == s[right]){
                if(right - left + 1 > maxLen){
                    start = left;
                    maxLen = right - left + 1;
                }
                left--;
                right++;
            }
        }
        return s.substr(start,maxLen);
```

**Time Complexity :**

$$
O \left( n \cdot  n  \right)   
$$

## Longest Common Prefix

I/P : `["flower","flow","flight"]`

O/P : `"fl"`

- Declare a string lca equal to the first word of the vector .
- for each word in vector we will do a horizontal scan and select only those characters that match with the current word in the vector .
- Once we found a non-match value for the lca we will break from the loop and return the modified string .

```cpp
string longestCommonPrefix(vector<string>& strs) {
        string lca = strs[0];
	for(int i = 0 ; i<strs.size() ; i++){
			help(lca,strs[i]);
	}
	return lca;

void help(string &lca , string test){
	 string ans = "";
	 int len = min(lca.size() , test.size());
	 for(int i = 0 ; i<len ; i++){
	 	if(lca[i] == test[i]){
	 		ans += test[i];
	 	}
		 else {
			 break;
		 }
	 }
	 lca = ans;
}
```

Time Complexity :

$$
O \left( n \cdot  m  \right)   
$$

## Check for Isomorphic strings

I/P : `s = "egg", t = "add"`
O/P : `true`

- We will create two map of <char,char> .
  first one will store all the string s to string t mappings .
- Run a for loop .
  We will do the mapping the the respective maps.
  With an If condition which will check weather the current mapping exist either of the maps , if it does then checking if the current character is similar to the previous one or not .

```cpp
bool isIsomorphic(string s, string t) {
     unordered_map<char,char> sTt , tTs;
     for(int i = 0 ; i<s.size() ; i++){
         char sTt_char = s[i];
         char tTs_char = t[i];

        if(sTt.find(sTt_char) != sTt.end() && sTt[sTt_char] != tTs_char){
            return false;
        }
        if(tTs.find(tTs_char) != tTs.end() && tTs[tTs_char] != sTt_char){
            return false;
        }

         sTt[s[i]] = tTs_char;
         tTs[t[i]] = sTt_char;
     }
     return true;
    }
```

Time Complexity :

$$
O \left ( n \right)
$$

Space Complexity :

$$
O \left( n+n  \right)   
$$

### Check weather strings are anagram or not

I/P :

`string s1 = "gram";
string s2 = "arm";`

O/P : `“no”`

Approach :

1. check the lengths of the two strings given
2. if the lengths are unequal then return false.
3. sort both the strings
4. Traverse both the strings simultaneously if any mismatch is found then return false else return true.

```cpp
int n1 = s1.length();
	int n2 = s2.length();
	if(n1!=n2){
		return false;
	}
	sort(s1.begin(),s1.end());
	sort(s2.begin(),s2.end());

	for(int i = 0 ; i<s1.size() ; i++){
		if(s1[i]!=s2[i]){
			return false;
		}
	}
	return true;
```

Time complexity : $O(nlogn + mlogm + n)$ , Space complexity : $O(1)$.

### Anagrams

Two strings are said to be anagrams if : <br>

1. One string can become another string and vice-versa.
2. Frequency of each character in the strings is same.
3. Size of strings should be same as well.

## Valid palindrome

I/P : -
`js = "A man, a plan, a canal: Panama"`

O/P : `true`

> Make sure that you can also encounter non alphanumeric characters also so handle them as well.

**Thinking** :

1. We can use two pointers approach to solve this problem.
2. Move both the pointers until start pointer is less than or equal to the end pointer.
3. Skip the characters which are not alphanumeric.

**Logic**for**not**aplphanumeric\_\_:

```cpp
bool isAlphanumeric(char c) {
  return (c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z') ||
         (c >= '0' && c <= '9');
}
```

**Code** 💻:

```cpp
bool isPalindrome(string s) {
  int start = 0, end = s.size() - 1;
  while (start < end) {
    while (start < end && !isAlphanumeric(s[start])) {
      start++;
    }
    while (end > start && !isAlphanumeric(s[end])) {
      end--;
    }
    if (tolower(s[start]) != tolower(s[end])) {
    }
    start++;
    end--;
    return false;
  }

  return true;
}
```

Time complexity : $O(n)$, Space complexity is constant.
