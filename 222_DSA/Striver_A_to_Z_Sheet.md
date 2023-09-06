# Binary Search
### [33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)#tricky
1. Check if middle element is `target` and if true return that index
2. Check which part of the array is sorted
3. If left part is sorted
	1. If `target` >= `left element` and `target` <= `middle element`, go left
	2. Else go right
4. Else right part is sorted definitely
	1. If `target` >= `middle element` and `target` <= `right element`, go right
	2. Else go left
5. **If array contains duplicate there can be cases like** : 
	1. `[1, 1, 2, 1, 1, 1], target = 2`
	2. Although using above algo we will find here that left part is sorted, it is actually not
	3. So we need to decrease the search space.
6. TC O(log N) 
7. SC O(1)
#### Code
```cpp
class Solution {
public:
    int search(vector<int>& a, int target) {
        int n = a.size();
        int l = 0, r = n-1;
        while(l<=r){
            int m = (l+r)>>1;
            if(a[m]==target)
                return m;
            // IN CASE ARRAY CONTAINS DUPLICATES
			if(a[m]==a[l] and a[m]==a[r])
            {
                l++,r--;
                continue;
            }
            //check which part is sorted (left or right part)
            if(a[l]<=a[m]){
                //target in left part
                if(a[l]<=target and target<=a[m])
                    r = m-1;
                //target in right part
                else
                    l = m+1;
            }
            else{
                //target in right part
                if(target>=a[m] and target<=a[r])
                    l = m+1;
                //target in left part
                else
                    r = m-1;
            }
        }
        return -1;
    }
};
```

### [153. Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)#tricky
#### My own Algo
1. Visualize array elements as points in a 2D space
2. If `(mid==0 or mid <= left) and (mid==n-1 or mid <= right)` then it is pivot element, so `ans = mid` and break from the loop.
3. If `mid < left` go left
4. Else :
	1. If `mid < right` go left
	2. Else go right
##### Code
```cpp
int findMin(vector<int>& a) {
        int ans=INT_MAX, n=a.size(), l=0, r=n-1;
        while(l<=r){
            int m =(l+r)>>1;
            if((m==0 or a[m-1]>=a[m]) and (m==n-1 or a[m+1]>=a[m]))
            {
                ans = a[m];
                break;
            }
            if(a[m]<a[l])
                r=m-1;
            else{
                if(a[r]<a[m])
                    l=m+1;
                else
                    r=m-1;
            }
        }
        return ans;
    }
```
#### Preferred Algo (Works For duplicates also)
1. If there is only one element return it.
2. If `mid == right element` do `right--`
3. Else if `mid > right element` do `left = mid + 1`
4. Else do ` right = mid`
5. return `left element` (we are doing `while(left < right)` so that's why)
##### Code
```cpp
int findMin(vector<int>& a) {
        int l=0,r=a.size()-1;
        while(l<r){
            int m=(l+r)>>1;
            //CHECK FOR DUPLICATE
            if(a[m]==a[r])
                r--;
            else if(a[m]>a[r])
                l=m+1;
            else
                r=m;
        }
        return a[l];
    }
```

### [540. Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)#tricky
1. Observe that before `target` element is seen `arr[odd_index] = arr[odd_index-1] and arr[even_index] == arr[even_index+1]`, but after the `target` element is seen, the condition is flipped.

1. If there is only one element return it
	1. If `mid index` is odd :
		1. It should match `prev element`
		2. If `mid element == prev element` then right side contains `target` element, so do `left = mid + 1`
		3. Else `mid element` is a potential answer, so make `right = mid`
	2. If `mid index` is even :
		1. It should match the `next element`
		2. If `mid element == next element` then right side contains `target` element, so do `left = mid + 2`
		3. Else `mid element` is a potential answer, so make `right = mid`

#### Code
```cpp
int singleNonDuplicate(vector<int>& a) {
        int n = a.size(),l = 0, r= n-1;
        if(n==1)
            return a[0];
        
        while(l<r){
            int m = (l+r)>>1;
            //if m is odd should match with prev element
            if(m & 1){
                if(a[m]==a[m-1])
                    l=m+1;
                else
                    r = m;
            }
            else{
                if(a[m]==a[m+1])
                    l=m+2;
                else
                    r = m;
            }
        }
        return a[l];
    }
```

### [162. Find Peak Element](https://leetcode.com/problems/find-peak-element/)#tricky
1. If `(mid == 0 or a[mid]>a[mid-1]) and (mid==n-1 or a[mid]>a[mid+1])` return `a[mid]`
2. Else if `mid == 0 or a[mid] >= a[mid-1]` go right
3. Else go left
```cpp
    int findPeakElement(vector<int>& a) {
        int n = a.size(), l = 0 , r = n-1;
        while(l<=r){
            int m = (l+r)>>1;
            if((m==0 or a[m]>a[m-1]) and (m==n-1 or a[m]>a[m+1]))
                return m;
            if(m==0 or a[m]>=a[m-1])
                l = m+1;
            else
                r = m-1;
        }
        return -1;
    }
```

### [1539. Kth Missing Positive Number](https://leetcode.com/problems/kth-missing-positive-number/)#tricky

### [K-th Element of Two Sorted Arrays - Coding Ninjas](https://www.codingninjas.com/studio/problems/k-th-element-of-2-sorted-array_1164159?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)#tricky

### [Median of Two Sorted Arrays - LeetCode](https://leetcode.com/problems/median-of-two-sorted-arrays/)#tricky

### [Minimize Max Distance to Gas Station - Coding Ninjas](https://www.codingninjas.com/studio/problems/minimise-max-distance_7541449?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)#tricky
1. partition 2 arrays such that max of 2 left parts is <= min of 2 right parts.
2. Binary search on the length of smaller array
3. Move right if `r1 < l2`
4. Else move left.

# Linked List ( ADVICE : Always Check For NULL )
## EASY
### [237. Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/)
- We are given a node not Head
- copy next node value and point to next to next node
- TC O(1)
- SC O(1)

### [Count nodes of linked list](https://www.codingninjas.com/studio/problems/count-nodes-of-linked-list_5884?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)
- use fast, slow pointer
-  Initially `fast = slow = head;`
- TC O(N)
- SC O(N)

### [Search in a Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/search-in-a-linked-list_975381?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)
- TC O(N)
- SC O(1)

### [Introduction To Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/introduction-to-linked-list_8144737?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)
- TC O(N)
- SC O(N)
```Cpp
Node* head = NULL;
Node* temp = NULL;
for(auto val:arr){
	Node* newNode = new Node(val);
	if(head==NULL)
	{
		head = temp = newNode;
	}
	else{
		temp->next = newNode;
		temp = temp->next;
	}
}
return head;
```
### [Insert Node At The Beginning - Coding Ninjas](https://www.codingninjas.com/studio/problems/insert-node-at-the-beginning_8144739?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)
- TC O(1)
- SC O(1)
### [Introduction To Doubly Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/introduction-to-doubly-linked-list_8160413?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)
```Cpp
Node* constructDLL(vector<int>& arr) {
    Node* head,*temp;
    head = temp = NULL;
    for(auto val:arr){
        Node* node = new Node(val);
        if(head==NULL){
            head = temp = node;
            continue;
        }
        else{
            temp->next = node;
            node->prev = temp;
            temp = node;
        }
    }
    return head;
}
```
### [Insert at end of Doubly Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/insert-at-end-of-doubly-linked-list_8160464?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)
```Cpp
Node * insertAtTail(Node *head, int k) {
    if(!head)
        return new Node(k);
    Node* temp = head;
    while(temp->next)
        temp = temp->next;
    Node* node =new Node(k);
    temp->next = node;
    node->prev = temp;
    return head;
}
```
### [Delete Last Node of a Doubly Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/delete-last-node-of-a-doubly-linked-list_8160469?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)
```Cpp
Node * deleteLastNode(Node *head) {
    if(!head or head->next==NULL)
        return NULL;
    Node* temp_head = head;
    while(temp_head->next != NULL)
        temp_head = temp_head->next;
    temp_head->prev->next = NULL;
    delete temp_head;
    return head;
}
```
### [Reverse A Doubly Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/reverse-a-doubly-linked-list_1116098?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)

```Cpp
if(!head)
	return NULL;
Node* nxt,*cur;
cur = nxt = head;
while(cur){
	nxt = cur->next;
	cur->next = cur->prev;
	cur->prev = nxt;
	if(!nxt)
		break;
	cur =nxt;
}
return cur;
```

## MEDIUM
### [Delete all occurrences of a given key in a doubly linked list - Coding Ninjas](https://www.codingninjas.com/studio/problems/delete-all-occurrences-of-a-given-key-in-a-doubly-linked-list_8160461?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf&leftPanelTab=0)
1. If `cur_node == key`
	1. `cur_node -> prev -> next = cur_node -> next`
	2. `cur_node -> next -> prev = cur_node -> prev`
2. Else if `newHead == NULL` do :
	1. `newHead = cur_node`
3. TC O(N)
4. SC O(1)


### [Remove duplicates from a sorted Doubly Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/remove-duplicates-from-a-sorted-doubly-linked-list_2420283?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)
1. Check if `cur_node == prev_node`
	1. If `true` then do `cur_node -> prev -> next = cur_node -> next` and `cur_node -> next -> prev = cur_node -> prev`
2. TC O(N)
3. SC O(1)


### [876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)
1. Use `slow and fast` pointer technique.
2. TC O(N)
3. SC O(1)

### [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
1. Maintain `pre`, `cur`, `nxt` pointer in iterative version
2. For recursive version do :
```cpp
void go(ListNode* node,ListNode*& newHead){
    if(!node)
        return;
    if(!node->next){
        newHead = node;
        return;
    }
    go(node->next,newHead);
    node->next->next = node;
    node->next = NULL;
}
```
3. TC O(N)
4. SC O(1) in iterative version and O(N) in recursive version


### [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)#tricky
#### Proof of Time Complexity O(N)
- If the list has **N** nodes, then in **<= N** steps, either the fast pointer will find the end of the list, or there is a loop and the slow pointer will be in the loop.

- Lets say the loop is of length **M <= N**: Once the slow pointer is in the loop, both the fast and slow pointers will be stuck in the loop forever. Each step, the distance between the fast and the slow pointers will increase by 1. When the distance is divisible by **M**, then the fast and slow pointers will be on the same node and the algorithm terminates. The distance will reach a number divisible by **M** in **<= M** steps.

- So, getting the slow pointer to the loop, and then getting the fast and slow pointers to meet takes **<= N + M <= 2N** steps, and that is in **O(N)**

- In fact, you can get a tighter bound on the step count if you note that when there's a loop, the slow pointer will get to it in **N - M** steps, so the total step count is **<= N**.
#### Code
```cpp
    bool hasCycle(ListNode *head) {
        ListNode* slow = head , *fast = head;
        while(fast and fast->next){
            fast = fast->next->next;
            slow = slow->next;
            if(fast == slow)
                return true;
        }
        return false;
    }
```

### [142. Linked List Cycle II](https://leetcode.com/problems/linked-list-cycle-ii/)#tricky
#### Proof
- Gaurav sen video
### [234. Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)#tricky

1. Reverse up to the middle using `fast slow pointer` technique.
2. Then start checking for palindrome from middle.
3. Take care of odd / even length case
4. `while(fast and fast->next)` should be used instead of `while(fast->next and fast->next->next)` 
5. TC O(N) 
6. SC O(1)

### [328. Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/)#tricky
1. Tricky Implementation
2. Maintain `even_head`, `even_tail`, `odd_head` and at the end do `even_tail->next = odd_head`
3. For each node `L1` let `L2 = L1->next`, then `L1->next = L2->next` and `L1 = L2`
```cpp
ListNode* oddEvenList(ListNode* head) {
        if(!head or head->next==NULL)
            return head;

        ListNode* even_head,*odd_head,*even_tail,*l2;
        even_head = odd_head = NULL;

        int i=0;
        for(ListNode* l1 = head;l1!=NULL;){
            l2 = l1->next;
            if(l2)
                l1->next = l2->next;
            if(i==0){
                if(even_head==NULL){
                    even_head = l1;
                }
                if(l1->next==NULL){
                    even_tail = l1;
                }
                i=1;
            }
            else{
                if(odd_head==NULL){
                    odd_head = l1;
                }
                i=0;
            }
            l1 = l2;
        }

        even_tail->next = odd_head;
        return even_head;
    }
```

### [19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
1. Maintain 2 pointers `L1` and `L2` having a distance n between them and move them until `L2` reaches the end.
2. Check if `head` is NULL or `head->next` is NULL, if true return NULL
3. Check if it is the First Node that needs to be deleted, then simply return `head->next`
4. TC O(N)
5. SC O(1)

### [2095. Delete the Middle Node of a Linked List](https://leetcode.com/problems/delete-the-middle-node-of-a-linked-list/)
1. use `fast slow pointer` technique
2. Check if there's no node or only one node present
3. Take care of even and odd length linked list
4. TC O(N)
5. SC O(1)

### [160. Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/)#tricky
1. TC O(N+M)
2. SC O(1)
```cpp
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode* a = headA , *b = headB;
        if(not a or not b)
            return nullptr;
        while(a!=b){
            a = (a == nullptr)?(headB):(a->next);
            b = (b == nullptr)?(headA):(b->next);
        }
        return a;
    }
};
```
### [445. Add Two Numbers II](https://leetcode.com/problems/add-two-numbers-ii/)#tricky
1. Since input lists may have different size it make sense to determine the sizes. At this step we also could normalize lists by prepending zero-nodes to the smaller list. But this approach will require additional memory, so we are going to ignore the normalization.
    
2. Iterate over the lists, compute the sum of items and put it into the resulting list. But here are the couple tricks: we are going to build the resulting list in the reversed order and we don't keep the carry value. For example:  
    ![image](https://assets.leetcode.com/users/peppered/image_1592152162.png)
    
3. Next we are going to normalize the resulting list. Starting form it's head (which contains the lowest order number) we will iterate over all nodes normalizing the value (`val % 10`), remembering the carry value and reversing the resulting list.
    
4. At the last step the carry value may be greater than 0. In that case we have to create a new node and make it a header of the result.
    

	![image](https://assets.leetcode.com/users/peppered/image_1592209145.png)

### [148. Sort List](https://leetcode.com/problems/sort-list/)#tricky

1. Using `fast-slow pointer` find the middle node of the list.
2. Now call `mergeSort` for 2 halves.
3. `Merge the Sorted List` (divide and conqueror Approach)
4. TC O(N logN)
5. SC O(1)

### [Sort linked list of 0s 1s 2s - Coding Ninjas](https://www.codingninjas.com/studio/problems/sort-linked-list-of-0s-1s-2s_1071937?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)#tricky

1. The 1st approach would be counting the number of occurrences of 0, 1, and 2. Then updating the data of the linked list in sorted order.
2. The 2nd approach would be separating the given linked list into 3 linked lists having 0s, 1s and 2s. Then reconnecting them in sorted fashion.
### [Add one to a number represented as Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/add-one-to-a-number-represented-as-linked-list_920557?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)
1. Reverse the List
2. Add one and remember to update the carry
3. Reverse the List again

###
## HARD

### [Reverse Nodes in k-Group - LeetCode](https://leetcode.com/problems/reverse-nodes-in-k-group/)#tricky
1. Calculate length of Linked List
2. If `Head == NULL or k == 1` return `Head`
3. Implement the function `Node* go(Node* head,int rem_len,int& k)`
	1. If `rem_len < k` return `head`
	2. Else reverse k nodes , then do `head->next = go(cur, rem_len - k, k)` and return `prev_node`


### [Rotate List By K from End- LeetCode](https://leetcode.com/problems/rotate-list/description/)#tricky
1. First get the length and do `k %= len`
2. If `k == 0` return `head`
3. 'If not, maintain 2 pointers `L1` and `L2` having a distance k between them and move them until `L2` reaches the end
4. Then the new Head will be `L1->next`, so just connect and disconnect links and return new Head.
5. TC O(N)
6. SC O(1)


### [Flatten A Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/flatten-a-linked-list_1112655?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)#tricky
1. put the head nodes of sub Linked Lists into a list 
2. Use merge sort to sort them 
3. return head node
4. TC O( NK log(NK) ) where N is list size and K is size of each subList
5. SC O(NK)
```cpp
//MERGE WITHOUT EXTRA SPACE
Node* merge(Node* l1,Node* l2){
    Node* head,*temp;
    if(l1->data<=l2->data)
        head = temp = l1,l1=l1->child;
    else
        head = temp= l2,l2=l2->child;

    while(l1 and l2)
    {
        if(l1->data <= l2->data){
            temp->child = l1;
            l1 = l1->child;
            temp = temp->child;
        }
        else{
            temp->child = l2;
            l2 = l2->child;
            temp = temp->child;
        }
    }

    if(l1)
        temp->child = l1;
    else
        temp->child = l2;
    return head;
}

Node* merge_sort(int l,int r,vector<Node*>& list){
    if(l==r){
        list[l]->next = NULL;
        return list[l];
    }

    else{
        int m = (l+r)>>1;
        Node* l1 = merge_sort(l,m,list);
        Node* l2 = merge_sort(m+1,r,list);
        return merge(l1,l2);
    }
}

Node* flattenLinkedList(Node* head) 
{
    if(!head or !head->next)
        return head;
    vector<Node*>list;
    Node* temp = head;
    while(temp)
        list.push_back(temp),temp= temp->next;
    int n = list.size();
    return merge_sort(0,n-1,list);
}
```


### [Copy List with Random Pointer - LeetCode](https://leetcode.com/problems/copy-list-with-random-pointer/)#tricky
1. Iterate the original list and duplicate each node. The duplicate of each node follows its original immediately.
	1. Original_node1 -> duplicate_node_1 -> original_node_2 -> duplicate_node_2
2. Iterate the new list and assign the random pointer for each duplicated node.
3. Restore the original list and extract the duplicated nodes.
4. TC O(N)
5. SC O(N)
```cpp
Node* copyRandomList(Node* head) {
         Node *newHead, *l1, *l2;
    if (head == NULL) return NULL;
    for (l1 = head; l1 != NULL; l1 = l1->next->next) {
        l2 = new Node(l1->val);
        l2->next = l1->next;
        l1->next = l2;
    }
        
    newHead = head->next;
    for (l1 = head; l1 != NULL; l1 = l1->next->next) {
        if (l1->random != NULL) l1->next->random = l1->random->next;
    }
        
    for (l1 = head; l1 != NULL; l1 = l1->next) {
        l2 = l1->next;
        l1->next = l2->next;
        if (l2->next != NULL) l2->next = l2->next->next;
    }

    return newHead;
    }
```
