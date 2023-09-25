
## Print all permutation of a number
The most optimal way to get all the permutation would be to apply backtracking to the process. 
```cpp
void permute(std::vector<int> &ds, std::vector<int> &mp, int n,
             std::vector<std::vector<int>> &ans) {
  if (ds.size() == n) {
    ans.push_back(ds);
    return;
  }
  for (int i = 1; i <= n; i++) {
    if (!mp[i - 1]) {
      mp[i - 1] = 1;
      ds.push_back(i);
      permute(ds, mp, n, ans);
      // Backtracking because for checking other paths we need to clear the current data structures first. 
      ds.pop_back(); 
      mp[i - 1] = 0;
    }
  }
}
```
Time complexity : $O(n!)$. 
## Sudoku Solver

Very Important Questions

To traverse each element of 3 x 3 matrix we do this .

`board[3*(row/3) + i/3][3*(col/3) + i%3] ith value will traverse from 0 to 9` 

To check weather the position is valid or not. 

```cpp
bool check(vector<vector<char>>& board , int row , int col , int value){
        for(int i = 0 ;i<9 ; i++){
            if(board[i][col] == value){
                return false;
            }
            else if(board[row][i]==value){
                return false;
            }
            else if(board[3*(row/3) + i/3][3*(col/3) + i%3] == value){
                return false;
            }
        }
        return true;
    }
```

Main Algorithm 

```cpp
bool solve(vector<vector<char>>& board){
         for(int i = 0 ;i<board.size() ; i++){
            for(int j = 0 ; j<board[0].size() ; j++){
                if(board[i][j] == '.'){
                    for(char c = '1' ; c<='9' ; c++){
                    if(check(board,i,j,c)){
                        board[i][j] = c;
                        if(solve(board)){
                            return true;
                        }
                        board[i][j] = '.'; // backtracking step
                    }
                }
                    return false;
                }   
            }
        }
        return true;
    }
```

Time complexity : $O(n^2*n^9)$ . 

## M Coloring

Given a graph and some color in such a way that adjacent nodes do not have same color.

We will be requiring an additional color vector which will store the color stored in all the nodes of the graph. 

Main Algorithm : 

```cpp
bool solve(int node , bool graph[101][101], vector<int> &color , int m , int n){
        if(node == n){
            return true;
        }
        for(int i = 1 ; i<=m ; i++){
            if(canColor(node,graph,color,m,n,i)){
                color[node] = i;
                if(solve(node + 1 , graph , color, m , n)){
                    return true;
                }
                color[node] = -1; // Backtracking step
            }
        }
        return false;
    }
```

For checking weather the node can be colored with the given color by checking all its neighbors . 

```cpp
bool canColor(int node ,bool graph[101][101] , vector<int> &color , int m , int n , int newColor){
        for(int k = 0 ; k<n ;k++){
            if(k!=node && graph[node][k] == 1 && color[k] == newColor){
                return false;
            }
        }
        return true;
    }
```

Time Complexity : $O(M^N$) , Space complexity : $O(n+n)$.
## N-Queen 
<span style='color:red;'>Very Important Question for placement</span>
You need to place all the n queens into a chess board of size n x n matrix, in such a position that none of the queen could attack each other. 
Approach : 
- We will do very layman approach for this problem 
- Try out all the possible position for the queen to be placed. 
- When we find out that we are not able to put the queen in any of the position then we backtrack to the previous state because we know that, exploring that particular state will not give us the answer at any moment. 
```cpp
void help(int col, std::vector<std::vector<std::string>> &ans,
          std::vector<std::string> &board, int n) {
  if (col == n) {
    ans.push_back(board);
    return;
  }
  for (int i = 0; i < n; i++) {
    if (canPut(i, col, board, n)) {
      board[i][col] = 'Q';
      help(col + 1, ans, board, n);
      board[i][col] = '.'; // This is the backtracking step
    }
  }
  return;
}
```
The above code is the main algorithm 

To check weather we can put a queen at the particular position we do some checks. 
```cpp
bool canPut(int row, int col, std::vector<std::string> &board, int n) {
  int dup_row = row, dup_col = col;

  while (dup_row >= 0 && dup_col >= 0) {
    if (board[dup_row][dup_col] == 'Q') {
      return false;
    }
    dup_row--;
    dup_col--;
  }
  dup_row = row, dup_col = col;
  while (dup_col >= 0) {
    if (board[dup_row][dup_col] == 'Q') {
      return false;
    }
    dup_col--;
  }
  dup_row = row, dup_col = col;
  while (dup_col >= 0 && dup_row < n) {
    if (board[dup_row][dup_col] == 'Q') {
      return false;
    }
    dup_col--;
    dup_row++;
  }
  return true;
}
```
👆The above code is to check all the possible directions for the current queen conflicts. 

Time complexity : $O(n!)$ . 

## Permutation Sequence
A number n will be given them among all the n! permutations return the kth permutation from those permutations in lexicographically sorted manner. 
###### Brute force 
We can use recursion to generate all the permutations and sort them and finally return the kth permutation form sorted order. 
##### Optimal 
We will reduce the search space by selecting a particular element as starting element. 
```cpp
std::string solve(int n, int k) {
  std::string ans = "";
  std::vector<int> numbers;
  int fact = 1;
  for (int i = 1; i < n; i++) {
    fact = fact * i;
    numbers.push_back(i);
  }
  numbers.push_back(n);
  k = k - 1; // for zero based indexing
  while (true) {
    ans = ans + std::to_string(numbers[k / fact]);
    numbers.erase(numbers.begin() + k / fact);
    if (numbers.size() == 0) {
      break;
    }
    k = k % fact; // because we need to change out search for further search .
    fact = fact / numbers.size();
  }
  return ans;
}
```
$k/fact$ this give us the which chunk permutation to choose. 
$k\%fact$ will give us relative position in the new sub-group formed. 
The new k value point to which particular permutation you  are trying to find in the new group. 
**fact** this value tell us how many possible permutation for every numbers sequences. 
$fact/numbers.size()$ this will give the no of possible permutation for every reduced sequence. 
Time complexity : $O(n+n*n)$ , Space complexity : $O(n)$ to store the numbers vector. 
> vector.erase function takes $O(n)$ time. 

