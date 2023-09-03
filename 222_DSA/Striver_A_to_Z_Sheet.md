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
