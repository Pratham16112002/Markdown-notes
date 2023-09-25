

### find

This function is used to find the root of the given vertex.

Time complexity : $O(1)$. 

 

```cpp
int find(int x) { return root[x]; }
```

### Union

This function makes the root of the two vertex same. 

Time complexity : $O(n)$. 

```cpp
void unionMethod(int x, int y) { // Takes O(n)
    int Parent_x = find(x);
    int Parent_y = find(y);
    if (Parent_x != Parent_y) {
      for (int i = 0; i < root.size(); i++) { // Takes O(n) time complexity
        if (root[i] == Parent_y) {
          root[i] = Parent_x;
        }
      }
    }
    return;
  }
```

### Same Nodes

To check weather two nodes belong to the same set or not. 

```cpp
bool isSame(int x , int y){
	return find(x) == find(y)
}
```

Time complexity : $O(1)$. 

## Quick Union

Worst case of find , union , checkConnected is $O(n)$ . 

```cpp
#include <bits/stdc++.h>
#include <iostream>

class QuickUnion {
public:
  std::vector<int> root;
  QuickUnion(int size) {
    root.resize(size);
    for (int i = 0; i < size; i++) {
      root[i] = i;
    }
  }
  int find(int x) {
    while (root[x] != x) {
      x = root[x];
    }
    return x;
  }
  void unionMethod(int x, int y) {
    int P_x = find(x);
    int P_y = find(y);
    if (P_x != P_y) {
      root[P_y] = P_x;
    }
  }
  bool isSame(int x, int y) { return find(x) == find(y); }
};

int main() {
  QuickUnion un(6);
  un.unionMethod(0, 1);
  un.unionMethod(1, 2);
  un.unionMethod(3, 5);
  std::cout << un.isSame(0, 4) << std::endl; // 0
  std::cout << un.isSame(1, 2) << std::endl; // 1
  std::cout << un.isSame(4, 5) << std::endl; // 0
  return 0;
}
```

## Spanning tree

> A Tree which has N nodes and N -1 edges and each nodes is reachable to each other .
> 

There are multiple Spanning tree possible for a given tree . 

## Minimum Spanning tree

> A Spanning tree with minimum sum is called a Spanning tree .
> 

For finding MST :

1. Prims Algorithm . 
2. Kruskal’s Algorithm . 

## Prims Algorithm

**Data structures :** 

1. Priority Queue ( min heap ) . 
2. Visited Array .

Algo : 

- Create required data structures array .
- Push the node 0 with 0 weight in the queue .
- Until the queue is empty .
    1. Get the node and weight from the min heap.
    2. Check if the node is visited or not . 
    3. If visited then ⇒ step 4 . else step 5 
    4. Traverse its adjacent nodes and again check if the child node is visited or not . 
        1. if not visited : then push it into out mi heap . 
        2. else : do nothing . 
    5. continue . 

```tsx
int spanningTree(int V, vector<vector<int>> adj[])
    {
        vector<int> vis(V,0);
        priority_queue<pair<int,int> , vector<pair<int,int>> , greater<pair<int,int>>> pq;
        pq.push({0,0});
        int sum = 0;
        while(!pq.empty()){
            auto curr_node = pq.top();
            pq.pop();
            int node = curr_node.second;
            int wt = curr_node.first;
            
            if(vis[node] == 1) continue;
            vis[node] = 1;
            sum += wt;
            for(auto it : adj[node]){
                int weight_c = it[1];
                int node_c = it[0];
                if(!vis[node_c]){
                pq.push({weight_c,node_c});    
                }
                
            }
            
        }
        return sum;
    }
```

Time Complexity : 

$$
O \left( v+v+v. \log\left( v  \right)  + { v  }^{ 2  }  . \log\left( v  \right)    \right)   
$$

## Disjoint Set

Used to find weather the two component belong to the same component tree or not. 

**Functionality** : 

1. Find Parent ⇒ in constant time. 
    1. We will take two arrays rank array and parent array. 
2. Union 

**Pseudo code:**

1. Find the ultimate parent of u and v as pu and pv. 
2. Find the rank of pu and pv. 
3. Connect the smaller rank to the larger rank. 
    
    While doing `findParent()` we need to path compression , to reduce the time complexity from log(n) to constant. 
    
    **Path Compression :** 
    
    It is a technique used to optimize the performance of union operation in Quick Union . 
    
    ![](https://i.imgur.com/ElphtC0.png)

    
    While path compression we cannot reduce the rank. 
    

Q: **Why we always connect smaller component to bigger component** ?

A: When we connect a smaller to a bigger component we try to make the complexity for the path compression much more faster .

Path compression is a recursive algorithm , by adding the smaller component we are not increasing the height of the bigger component which helps us to reduce the time complexity for the path compression. 

Time Complexity : 

$$
O \left( const  \right)  
$$
>For the first time the path compression takes time equal to the depth of the parent tree formed.

Algorithm for path compression: 

```cpp
findParent(u) {
	if(u == parent(u)){
return u;
}
return findParent(parent[u]);
}

```

Code: 

```cpp
#include <iostream>
#include <vector>

using namespace std;

class DisjointSet {
	vector<int> rank , parent, size;
public:
	DisjointSet(int n){
		rank.resize(n+1,0);
		parent.resize(n+1);
		size.resize(n+1,1);
		for(int i = 0 ; i<parent.size() ; i++){
			parent[i] = i;
		}

	}
	int findUltiPar(int u){
		if(u == parent[u]){
			return u;
		}
		return parent[u] = findUltiPar(parent[u]);
	}
	void unionFindByRank(int u , int v){
		int ul_u = findUltiPar(u);
		int ul_v = findUltiPar(v);
		if(ul_v == ul_u){
			return;
		}
		if(rank[ul_v] < rank[ul_u]){
			parent[ul_v] = ul_u;
		}
		else if(rank[ul_v] > rank[ul_u]){
			parent[ul_u] = ul_v; 
		}
		else {
			parent[ul_u] = ul_v;
			rank[ul_v]++;
		}
	}
	void unionFindBySize(int  u , int v){
		int ul_u = findUltiPar(u);
		int ul_v = findUltiPar(v);
		if(ul_v == ul_u){
			return ;
		}
		if(size[ul_v] > size[ul_u]){
		   parent[ul_u] = ul_v;
		   size[ul_v]+=size[ul_u];
		}
		else {
			parent[ul_v] = ul_u;
			size[ul_u]+=size[ul_v];
 		}
	}
};

int main(int argc, char const *argv[])
{
		 #ifndef ONLINE_JUDGE
    // For getting input from input.txt file
    freopen("input1.txt", "r", stdin);
    // Printing the Output to output.txt file
    freopen("output1.txt", "w", stdout);
    #endif

DisjointSet ds(7);
ds.unionFindBySize(2,3);
ds.unionFindBySize(4,5);
ds.unionFindBySize(6,7);
ds.unionFindBySize(5,6);
if(ds.findUltiPar(3) == ds.findUltiPar(7)){
	cout<<"same"<<endl;
}
else{
	cout<<"not same"<<endl;
}
ds.unionFindBySize(3,7);  
if(ds.findUltiPar(3) == ds.findUltiPar(7)){
	cout<<"same hi "<<endl;
}
else{
	cout<<"not same"<<endl;
}
return 0;
}
```

## Kruskal’s Algorithm

Pre-Knowledge : Disjoint Sets
Algo : 

- First we need to sort all the edges by their weights.
- Traverse each sorted edge and apply union operation of the disjoint set Data Structure.
- Before applying union Operation we need to check weather the the nodes belong to the same parent or not.

Code:

```cpp
int spanningTree(int V, vector<vector<int>> adj[])
    {
        vector<pair<int,pair<int,int>>> edges; // This will store edges as ({{wt} ,{ u , v}}).
        for(int i = 0 ; i<V ; i++){
            for(auto it : adj[i]){
                int adjNode = it[0];
                int wt = it[1];
                 int node = i;
            edges.push_back({wt,{node,adjNode}});
            }
        } // O(V + E) . 
        sort(edges.begin() , edges.end()); // Suppose their are M edges O(M Log(M)) . 
        DisjointSet ds(V);
        int mstWeight = 0;
        for(int i = 0 ; i<edges.size() ; i++){
            int wt = edges[i].first;
            int u = edges[i].second.first;
            int v = edges[i].second.second;
            if(ds.findUltiPar(u) != ds.findUltiPar(v)){
                mstWeight+=wt;
                ds.unionFindBySize(u,v);
            }
        }  // O(M x ( 4 x alpha )). 
        return mstWeight;
        
    }
```

Time Complexity  : 

$$
O \left(  \left( V+E  \right)  +M \log\left( M  \right)  + \left( M. \left( 4.Apha \cdot  2  \right)    \right)    \right)   
$$
>Where M is the number of edges

Space Complexity : 

$$
O \left( N+N+M  \right)  
$$
>First N for the size array . Second N for the parent array . M for the edges vector.