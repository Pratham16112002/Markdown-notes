[[MST Disjoint Set]]
[[Shortest Path Algorithm]]

## Number of Provinces

Tell the number of graph components which are connected to each other and also them self , Note each node of the connected component should be reachable among them.

I/P :  ![](https://i.imgur.com/Ciz5Y4J.png)

O/P : The number of such connected components ⇒ 2 .

Approach :

- Convert to an Adjacency list .
    
    Only if Adjacency Matrix is given . 
    
- Create a visited vector initially with zeros.
- Call the dfs for each vertex through a for loop.

```cpp
class Solution {
public:
    void dfs(int node , vector<int> adj[] , vector<int> &vis){
        vis[node] = 1;
        for(auto it : adj[node]){
            if(!vis[it]){
                dfs(it,adj,vis);
            }
        }
    }
    int findCircleNum(vector<vector<int>>& isConnected) {
        int N = isConnected.size();
        vector<int> adj[N];
        for(int i = 0 ; i<isConnected.size() ; i++){
            for(int j = 0 ; j<isConnected[0].size() ; j++){
                if(isConnected[i][j] == 1 && i!=j){
                    adj[i].push_back(j);
                    adj[j].push_back(i);
                }
            }
        }
        int count = 0;
        vector<int> vis(N,0);
        for(int i = 0 ; i<N ; i++){
            if(!vis[i]){
                count++;
                dfs(i,adj,vis);
            }
        }
        return count;

    }
};
```

Space Complexity : 

$$
O \left( n+n  \right) 
$$

Time Complexity : 

$$
O \left( n+dfs \left( V+2E  \right)    \right)   
$$

## Flood Fill Algorithm

You will be given a N X N grid and a starting row and column index , and a new color you need to color all the adjacent places with the new color ( remember you can only color only those neighbors having same color as the starting cell color ) and continue this process until all the connected colors are colored . 
![](https://i.imgur.com/UwQ4IPs.png)

Both BFS and DFS can be applied to this problem.

- First we will get the color of the source node from the given matrix .
    
    Create another matrix as answer . 
    Create two arrays del row and del col for traversing all the directions of the current matrix . 
    
- Then we will call the dfs .
    
    marking the cell with the new color defined . 
    
- Run for loop for all four direction .
    
    after checking all the valid conditions we call the dfs for the neighbor nodes. 
    

```cpp
class Solution {
public:
    void dfs(int row , int col , vector<vector<int>> &image , vector<vector<int>>& ans , int del_row[] , int del_col[] , int iniColor , int newColor){
        ans[row][col] = newColor;
        int m = ans.size();
        int n = ans[0].size();
        for(int i= 0 ; i<4 ; i++){
            int n_row = row + del_row[i];
            int n_col = col + del_col[i];
// these are the conditions for the new node that needs to be colored . 
            if(n_row >= 0 && n_row < m && n_col >= 0 && n_col < n && image[n_row][n_col] == iniColor && ans[n_row][n_col] != newColor) {
                dfs(n_row,n_col , image , ans , del_row , del_col , iniColor , newColor);
            }
        }
    }
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
      int  iniColor = image[sr][sc] ; // getting the color of the source node and making it as our initial color 
// very important part 
        int del_row [] = {-1 , 0  , 1 , 0};
        int del_col [] = {0 , 1 , 0 , -1};
        vector<vector<int>> ans = image;
        dfs(sr,sc, image , ans , del_row , del_col , iniColor , color);
        return ans;

    }
};
```

Time Complexity : 

$$
O \left( x+ \left( x \cdot  4  \right)    \right)   
$$
> x ⇒ n * m and x * 4 is because of the for loop for traversing all its neighbors.

Space Complexity : 

$$
O \left( m \cdot  n+m \cdot  n  \right)   
$$
>first m*n is the matrix you are using to store the given matrix which is not counted if we altering the given current array , and second m*n is because of the recursion stack space that we are using .
## Number of islands

I/P : 

```
grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
```

O/P : 1 

You need to output the number of distinct islands that can be formed using only 1’s in the matrix, and 0 represents ocean in between. 

Their are two  variants of this problem where also the diagonal 1’s are also considered as the part of  the island. 

Algo : 

- Create a visited 2d vector of size same as the grid size.
- Traverse the 2d grid .
    
    call the bfs only if grid cell has ‘1’ and it is not already visited . 
    

BFS : 

```cpp
void bfs(int row , int col , vector<vector<int>> &vis , vector<vector<char>> &grid){
        vis[row][col] = 1;
        queue<pair<int,int>> q;
        int del_row[] = {-1,0,1,0};
        int del_col[] = {0,1,0,-1};
        q.push({row,col});
        while(!q.empty()){
            int row = q.front().first;
            int col = q.front().second;
            q.pop();
            for(int i = 0 ;i<4 ; i++){ // this only traverse in all the four directions only not the diagonal ones. 
                int new_r = row + del_row[i];
                int new_c = col + del_col[i];
                if(new_r >= 0 && new_r <grid.size() && new_c >= 0 && new_c < grid[0].size() && vis[new_r][new_c] == 0 && grid[new_r][new_c] == '1' ){
                    vis[new_r][new_c] = 1;
                    q.push({new_r,new_c});
                 }
            }
        }
    }
```

Time Complexity : 

$$
O \left(  { n  }^{ 2  }   \cdot  9+ { n  }^{ 2  }    \right)   
$$

Space Complexity:  

$$
O \left(  { n  }^{ 2  }  + { n  }^{ 2  }    \right)   
$$

## Kosa_raju’s Algorithm

> Suppose their exist two nodes both the nodes are said to be strongly Connected components , if both node can reach each other .
> 

Algo : 

- First we need to do the topological sort of the given graph.
- We need to create a transpose graph of the given graph.
    
    Need while doing transpose mark each and every node in the visited array as unvisited for the transposed graph traversal. 
    
- Call the DFS using the transposed graph.

```cpp
#include <iostream>
#include <vector>
#include <stack>

using namespace std;

void dfs(int node, vector<int> adj[], vector<int> &vis, stack<int> &st) {
    vis[node] = 1;
    for (auto it : adj[node]) {
        if (!vis[it]) {
            dfs(it, adj, vis, st);
        }
    }
    st.push(node);
}

void revDFS(int node, vector<int> &vis, vector<int> transpose[]) {
    vis[node] = 1;
    for (auto it : transpose[node]) {
        if (!vis[it]) {
            revDFS(it, vis, transpose);
        }
    }
    cout << node << " ";
}

int main() {
    ios::sync_with_stdio(0);
    cin.tie(0);

    int n = 5;
    vector<int> adj[n];
    adj[1].push_back(2);
    adj[2].push_back(4);
    adj[2].push_back(3);
    adj[3].push_back(1);
    adj[4].push_back(5);

    stack<int> st;
    vector<int> vis(n, 0);
    for (int i = 0; i < n; i++) {
        if (!vis[i]) {
            dfs(i, adj, vis, st);
        }
    }

    vector<int> transpose[n];
    for (int i = 0; i < n; i++) {
        vis[i] = 0;
        for (auto it : adj[i]) {
            transpose[it].push_back(i);
        }
    }

    while (!st.empty()) {
        int node = st.top();
        st.pop();
        if (!vis[node]) {
            cout << "SCC: ";
            revDFS(node, vis, transpose);
            cout << endl;
        }
    }

    return 0;
}
```

Time Complexity : 

$$
O \left(  \left( n+e  \right)   \cdot  3  \right)   
$$

Space Complexity : 

$$
O \left(  \left( n+e  \right)  +n+n  \right)   
$$