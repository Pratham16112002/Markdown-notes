
# Reverse a Linked List

Most asked Question in an interview. 

As we require the nodes in reverse order we could try a data structure which is Last In first Out.

Approach : 

1. Push each node in the stack.
2. Retrieve each node again and push them into a new linked list.

```cpp
ListNode* reverseList(ListNode* head) {
        if(head == NULL || head->next == NULL){
            return head;
        }
        stack<ListNode*> st;
        while(head!=NULL){
            st.push(head);
            head = head->next;
        }
        ListNode* newList = new ListNode(0);
        ListNode* newHead = newList;
        while(!st.empty()){
            int data = st.top()->val;
            newHead->next = new ListNode(data);
            newHead = newHead->next;
            st.pop();
        }
        return newList->next;
    }
```

Time complexity : $O(n+m)$ first n for traversing the linked list initially  and m is for travelling the stack until its empty , Space complexity : $O(m)$ , external stack used. 

Algo : 

- We will take two pointers initially pre = null  , cur = head.
- Traverse till head is not null.

```cpp
while(cur!=NULL){
            ListNode* nn = cur->next;
            cur->next = pre;
            pre = cur;
            cur = nn;
        }
        head = pre;
        return head;
```

Time Complexity : 

$$
O \left( n  \right) 
$$

Space Complexity : 

$$
O \left( 1  \right) 
$$

### Middle of the linked List

There are many approaches to solve this problem the best one the slow and fast pointer approach. 

Algo : 

- Fist we initialize two pointers called slow and fast.
- Traverse while the fast pointer and fast→next reaches the NULL end.
    
    fast is moved alternatively , where as slow pointer moves one by one. 
    
- At last we return the slow pointer which will always be at the middle position once the fast pointer reach the NULL end.

Code: 

```cpp
ListNode* slow = head;
        ListNode* fast = head;
        while(fast != NULL && fast->next != NULL){
            fast = fast->next->next;
            slow = slow->next;
        }
        return slow;
```

Time Complexity : 

$$
O \left(  \dfrac{ n  }{ 2  }    \right) 
$$
>More or less O(n).

Space Complexity : 

$$
O \left( 1  \right) 
$$

## Merge Two Sorted Linked List

Algo : 

- Create a new dummy node .
- Traverse while either of the given node becomes NULL .
    
    check the head of both the linked list compare it. 
    
    if List1 head is greater then List2 head then we point the temp head to the smaller one and move the head of that linked list to the next node. 
    
    else do the same with the list2 head . 
    
    always move the main temp head to the next node. 
    
- return DummyNode→next.

```cpp
ListNode* dummyNode = new ListNode(0);
        ListNode* tempNode = dummyNode;
        while(list1 != NULL && list2 != NULL){
            if(list1->val < list2->val){ // Comparing the two listhead values. 
                tempNode->next = list1; // Pointing to the next listNode. 
                list1=list1->next;
            }
            else {
                tempNode->next = list2;
                list2=list2->next;
            }
            tempNode = tempNode->next; // Moving the tempNode.  
        }
        while(list1 != NULL){
            tempNode->next = list1;
            list1=list1->next;
            tempNode = tempNode->next;
        }
        while(list2 != NULL) {
            tempNode->next = list2;
            list2 = list2->next;
            tempNode = tempNode->next;
        }
        return dummyNode->next;
```

Time Complexity : 

$$
O \left( N+M  \right)   
$$

Space Complexity : 

$$
O \left( 1  \right)  
$$
>Where N and M are the size of List 1 and List 2
## Delete the Nth Node from the end of the linked list

There are two ways to solve this problem. 

1. Brute Force. 
2. Fast and Slow pointer approach. 

Brute Force : 

```cpp
ListNode* temp = head;
        int counter = 0 ;
        while(temp!=NULL){
            temp = temp->next;
            counter++;
        }
        if(counter == n){ // Edge case when the n == length of the linked list. 
            head = head->next; // we just move the head to next node 
            return head; // return the head;
        }
        int key = counter - n;
        temp = head;
        while(key!=1){ // traveling to the right position 
            temp = temp->next;
            key--;
        }
        temp->next = temp->next->next; // pointer to the next->next node 
        return head; // returning the head 
```

Time Complexity : 

$$
O \left( N+N  \right)   
$$

Fast & Slow Pointer Approach

Algo : 

- Declare a dummy Node and point to head→next .
- Take two dummy nodes fast and slow pointer.
- move fast by one position to the next node for n times.
- move both slow and fast pointer by one position to the next node until fast→next ≠ NULL.
- `slow→next = slow→next→next`
- return `dummy→next;`

Code: 

```cpp
ListNode* dummy = new ListNode();
        dummy->next = head;
        ListNode* fast = dummy;
        ListNode* slow = dummy;
        for(int i = 0  ;i<n ; i++){
            fast = fast->next;
        }
        while(  fast->next !=NULL){
            fast = fast->next;
            slow = slow->next;
        }
       
        slow->next = slow->next->next;

        return dummy->next;
```

Time Complexity : 

$$
O \left( N  \right) 
$$
>Only for fast pointer traversal. 
## Adding Two Numbers using Linked List

This has no brute force approach so please confuse the interviewer 😁. 

Code: 

```cpp
ListNode* DummyNode = new ListNode(0);
        ListNode* temp = DummyNode;
        int carry = 0;
        while(l1 != NULL || l2 != NULL || carry != 0){
            int sum = 0;
            if(l1 != NULL){
                sum += l1->val;
                l1=l1->next;
            }
            if(l2 != NULL){
                sum += l2->val;
                l2=l2->next;
            }
            sum = sum + carry; // Adding the carry to the sum before creating a new node.
            ListNode* newNode = new ListNode(sum%10);
            carry = sum/10;
            temp->next = newNode; // Linking the new node to the temp ListNode. 
            temp = temp->next; // Moving to the next node 
        }
        return DummyNode->next; // Skipping the 0th node of the Linked List made and returning the next of it. 
```

Time Complexity : 

$$
O \left( max \left( NorM  \right)    \right)   
$$
>Where N and M are the length of Linked lists given to us.

Space Complexity : 

$$
O \left( n  \right)
$$
>Where n is the length of newly created linked list. 
## Find the intersection of the Two Linked list

Approaches : 

1. Brute Force : 
    1. For each node of one linked list we must traverse the entire other linked list to find the intersection. 
    Interviewer will not be happy 😜. 
    Time Complexity : 
    
    $$
    O \left( n \cdot  m  \right) 
    $$
    >where n and m are the length of linked list 1 and linked list 2. 
1. Hashing : 
    1. Hash the node address of one linked list. 
    2. Check for each address in the other linked list , if found a match then return the node , else return not found. 
    
    Time Complexity : 
    
    $$
    O \left( n+m \cdot   \log\left( n  \right)    \right)   
    $$
    > Assuming that the finding the address in the hash-table takes log(N) time where n is the size of the hash table.
3. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/u4FWXfgS8jw?si=dfbzPMLC8Dj7p8aT" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

1. Optimal 
    1. If Check any of the head is null or not. 
    2. Take two dummyNodes a and b . 
    3. Traverse till both the nodes becomes equal. 
        1. if a reaches null then make it point to head of other linked list. 
        2. if b reaches null then make it point to head of other linked list. 
    4. return a or b ( as your wish 😋 ). 

```cpp
if(headA == NULL || headB == NULL) {
            return NULL;
        }
        ListNode* a = headA;
        ListNode* b = headB;

        while(a!=b){
            a == NULL ? a = headB : a=a->next;
            b == NULL ? b = headA : b=b->next;
        }
        return a;
```

Time Complexity : 

$$
O \left( 2n  \right) 
$$
>In the worst case where no intersection exist we can say that it will traverse both the linked list once.