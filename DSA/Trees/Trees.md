
## Preorder traversal

Root → Left → Right 
We can also solve this traversal using recursion but it will take recursion stack space. 
Approach using stack : 

```cpp
vector<int> ans;
        if(root == NULL){ // to handle the case if only one null node is given 
            return ans;
        }
        stack<TreeNode*> st;
        st.push(root);

        while(!st.empty()){
            TreeNode* node = st.top();
            st.pop();
            ans.push_back(node->val);
            if(node->right){
                st.push(node->right);
            }
            if(node->left){
                st.push(node->left);
            }
        }
        return ans;
```
Time complexity : $O(n)$ , Space complexity : $O(n)$ i.e. is the stack space we are using. 

## Post-order traversal

Left → Right → Root
Basic approach should me the recursion approach. 
Stack approach :
```cpp
vector<int> ans;
        if(root == NULL){
            return ans;
        }
        TreeNode* curr = root;
        stack<TreeNode*> st;
        TreeNode* temp = NULL;
        while(curr!=NULL || !st.empty()){
            if(curr!=NULL){
                st.push(curr);
                curr = curr->left;
            }
            else {
                temp = st.top()->right;
                if(temp == NULL){
                    temp = st.top();
                    st.pop();
                    ans.push_back(temp->val);
                    while(!st.empty() && temp == st.top()->right){
                        temp = st.top();
                        st.pop();
                        ans.push_back(temp->val);
                    }              
              }
              else {
                  curr = temp;
              }
            }
        }
        return ans;
```
Time complexity : $O(2n)$ , first n for inserting the element in the stack then second n for check each and every element one by one , Space complexity : $O(n)$ , for the single stack we are using. 

## Left view of binary tree

I/P : 
*`4`*
*`/   \`*
*`5     2`*
*`/   \`*
*`3     1`*
*`/  \`*
*`6    7`*
O/P :
`4 5 3 6`
We need to move in the order : 
Root → Left → Right 
Approach : 
1. if the root is null then return 
2. if level is equal to the data structure size ( in which the answer is stored ) , we add the node into our answer , because it is the first node encountered while traversing each level.  
3. Call for the left tree with level = level + 1 
4. Call for the right tree with level = level + 1 

```cpp
void help(Node *root , int level , vector<int> &ds){
    if(root == NULL) return;
    if(ds.size() == level) { // we need to add the first element in the array for each level 
        ds.push_back(root->data);
    }
        help(root->left , level + 1 , ds);
        help(root->right,level+1,ds);
}
```
Time complexity : $O(N)$ , Space complexity : $O(H)$ , where H is the height of the tree.
## Find the ceil
You will be given a full binary tree and key , you need to find a node whose value is equivalent to $key$ or $key+1$.
<span style='color:yellow;'>Tried recursion didn't work 😪</span>
Approach : 
```cpp
int findCeil(BinaryTreeNode<int> *node, int x){
    int ceil = -1;
    while(node){
        if(node->data == x ){
            ceil = node->data;
            return ceil;
        }
         if(node->data < x){
            node = node->right;
        }
        else {
            ceil = node->data;
            node = node->left;
        }
    }
    return ceil;
}
```
Time complexity : $O(H)$ where H is the maximum height of the tree. 
What would be the worst case for the above algorithm 🧐? 
<span style='font-weight:bold;color:lightgreen;'>Skew Tree</span>
## Morris inorder traversal 
