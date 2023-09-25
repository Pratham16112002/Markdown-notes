## Dijkstra Algorithm

Similar to Shortest Path in Weighted graph . 

A source node and a destination node is given and you need to tell the shortest distance in terms of the edge weights of the graph. 

Two ways to implement this algorithm : 

1. Using Sets
2. Using Priority Queue

### Using Priority Queue

- First we will create a distance array.
    Setting initial distance to reach as infinity and the source node to zero . 
- Create a min heap .
- Push the Source node with distance zero in the min heap .
- Do while loop
    
    Extract the minimum node with its distance from the min heap. 
    
    Checking weather the its neighbor nodes are reachable with a new minimum distance if found. 
    
    If found then update the distance array and push the distance along with the node in the min heap. 
    

```cpp
vector<int> dist(vertices, 1e9);
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;

    pq.push({0, source});
    dist[source] = 0;

    while (!pq.empty()) {
        int currDistance = pq.top().first; // 
        int currNode = pq.top().second; // Combining both are taking complexity of O(log(v)) 
        pq.pop();

        for (auto it : adj[currNode]) { // takes worst case complexity of O(v^2)
            int neighbor_node = it.first;
            int neighbor_dis = it.second;

            if (currDistance + neighbor_dis < dist[neighbor_node]) {
                dist[neighbor_node] = currDistance + neighbor_dis;
                pq.push({dist[neighbor_node], neighbor_node});
            }
        }
    }

    return dist;
```

Time Complexity : 

$$
O \left( E \cdot   \log\left( v  \right)    \right)   
$$
>E = V^2
>Because no of time relaxation is called is equal to the number of edges in the graph .
### Shortest Path in a binary Maze

I/P : 

```
N=3, M=4
A=[[1,0,0,0],
   [1,1,0,1],
   [0,1,1,1]]
X=2, Y=3
```

O/P : 5 

Note zero is the dead cell we cannot path through it , if source and destination points to a zero cell then we simply return -1 ( because we cannot reach it ) . 

Solve is using Djikastra Algorithm . 

```cpp
vector<vector<int>> dist(N,vector<int>(M,1e9));
        dist[0][0] = 0; // marking the source as zero 
        queue<pair<int,pair<int,int>>> q;
        q.push({0,{0,0}}); // pushing the first node with distance zero in the queue
        int del_row[] = { -1 , 0 , 1 , 0 } ;
        int del_col[] = { 0 , 1 , 0 , -1 } ;
        while(!q.empty()){
            int curr_distance = q.front().first;
            int curr_x = q.front().second.first;
            int curr_y = q.front().second.second;
            q.pop();
            for(int i = 0 ;i<4 ; i++){
                int new_r = curr_x + del_row[i];
                int new_c = curr_y + del_col[i];
                if(new_r >= 0 && new_r < N && new_c >= 0 && new_c < M && A[new_r][new_c] == 1 && curr_distance + 1 < dist[new_r][new_c]){
                    q.push({curr_distance + 1 , { new_r , new_c}}); // all the necessary conditions for updated the answer . 
                    dist[new_r][new_c] = curr_distance + 1;
                    if(new_r == X && new_c == Y){
                        return curr_distance + 1;
                    }
                } 
            }
        }
        return -1;
```

Time Complexity : 

$$
O \left( E  \right)   
$$
>We removed the extra log(v) time complexity by using queue data structure instead of the priority queue .

## Shortest Path in Weighted Undirected Graph

**Similar to Djikastra’s algorithm** : Difference is we need to print the path with the minimum weight. 

Data Structures : 

1. Parent Array
2. Distance Array ( as before ) 
3. Priority Queue ( min Heap ) 

```cpp
vector<pair<int,int>> adj[n+1];
        for(auto it : edges){
            adj[it[0]].push_back({it[1],it[2]});
            adj[it[1]].push_back({it[0],it[2]});
        }
        priority_queue<pair<int,int>, vector<pair<int,int>>, greater<pair<int,int>>> pq;
        pq.push({0,1});
        vector<int> dist(n+1,1e9);
        dist[1] =0 ;
        vector<int> parent(n+1);
        for(int i = 1 ; i<=n ; i++){
            parent[i] = i;
        }
        while(!pq.empty()){
            auto curr_ele = pq.top();
            int curr_node = curr_ele.second;
            int curr_wt = curr_ele.first;
            pq.pop();
            for(auto it : adj[curr_node]){
                int adjNode = it.first;
                int adjNode_wt = it.second;
                if(curr_wt + adjNode_wt < dist[adjNode]){
                    dist[adjNode] = curr_wt + adjNode_wt;
                    pq.push({dist[adjNode],adjNode});
                    parent[adjNode] = curr_node;
                }
            }
        }
        if(dist[n] == 1e9){
            return {-1};
        }
        vector<int> ans;
        int final_node = n ; 
        while(parent[final_node] != final_node){
            ans.push_back(final_node);
            final_node = parent[final_node];
        }
        ans.push_back(1);
        reverse(ans.begin(),ans.end());
        return ans;
```

Time Complexity  : 

$$
O \left( E. \log\left( v  \right)  +n  \right)   
$$
>First term is the complexity of the djikastra’s algorithm and second is for the actual shortest path we are finding.

Space Complexity : 

$$
O \left( V+E  \right)   
$$

> Note : the Dijkstra’s algorithm cannot find the shortest path if the edge weights are negative Solution : Bellmen Ford Algorithm.
> 

## Bellmen Ford Algorithm

> **Negative Cycle** :
> ![](https://i.imgur.com/00m9nIm.png)


👆 The sum of the edges of the graphs is -2 , which is negative . 

Algo :

- We need to relax edges for N-1 times.

**Questions** : Why N-1 times ? 

**Ans :** Since in a graph of N nodes , in worst case , you will take N-1 edges from the first to last edge we required N-1 iterations. 

**Questions** : How we will detect a negative cycle. 

**Ans** : After the doing N-1 iterations we will do a final Nth iterations in which we will relax each edge and if any distance gets updated then it means that the graph contains negative cycle and we return -1 . 

```cpp
vector<int> dist(V,1e8);
        dist[S] = 0;
        for(int i = 0 ; i<V-1 ; i++){
            for(auto it : edges){
                int u = it[0];
                int v = it[1];
                int wt = it[2];
                if(dist[u]!= 1e9 && dist[u] + wt < dist[v]){
                    dist[v] = dist[u] + wt;
                }
            }
        }
        
        for(auto it : edges){
            int u = it[0];
            int v= it[1];
            int wt = it[2];
            if(dist[u]!= 1e9 && dist[u] + wt <dist[v]){
                return {-1};
            }
        }
        return dist;
```

 Time Complexity : 

$$
O \left( V \cdot  E+E  \right)   
$$
>O(V.E) for the first loop.

Space Complexity : 

$$
O \left( V  \right) 
$$
>V is the number of vertices. 

> Both Dijkstra’s algorithm and Bellmen Ford Algorithm are designed for single source shortest path.
> 

## Floyd Warshal Algorithm

Find the shortest distance between each and every  node in between  the graph. 

Helps to detect negative cycle. 

**Multi-source Shortest Path Algorithm**  

How to detect negative cycle in this algorithm. 

```cpp
for( int i = 0 ; i<n; i++){
	for (int j = 0 ; j<m ; j++) {
			if(matrix[i][j] < 0) {
				cout<<" Contains Negative Cycle "<<endl;
		}
	}
}
```

```cpp
int m = matrix.size();
	    int n = matrix[0].size();
	    for(int i = 0 ; i<m ; i++){
	        for(int j = 0 ; j<n ;j++){
	            if(matrix[i][j] == -1){
	                matrix[i][j] = 1e9;
	            }
	        }
	    }
	    for(int k = 0 ; k<m ; k++){
	         for(int i = 0 ; i<m ; i++){
	        for(int j = 0 ; j<n ; j++){
	            matrix[i][j] = min(matrix[i][j] , matrix[i][k] + matrix[k][j]);
	            }
	        }
	    }
	    for(int i = 0 ; i<m ; i++){
	        for(int j = 0 ; j<n ;j++){
	            if(matrix[i][j] == 1e9){
	                matrix[i][j] = -1;
	            }   
	        }
	    }
```

Time Complexity : 

$$
O \left(  { n  }^{ 3  }    \right)   
$$