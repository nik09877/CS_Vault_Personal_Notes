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
## HARD
### [Reverse Nodes in k-Group - LeetCode](https://leetcode.com/problems/reverse-nodes-in-k-group/)#tricky
1. Calculate length of Linked List
2. If `Hea`
3. Implement the function `Node* go(Node* head,int rem_len,int& k)`
	1. 
### [Rotate List By K from End- LeetCode](https://leetcode.com/problems/rotate-list/description/)#tricky
1. First get the length and do `k %= len`
2. If `k == 0` return `head`
3. 'If not, maintain 2 pointers `L1` and `L2` having a distance k between them and move them until `L2` reaches the end
4. Then the new Head will be `L1->next`, so just connect and disconnect links and return new Head.
5. TC O(N)
6. SC O(1)
### [Flatten A Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/flatten-a-linked-list_1112655?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)#tricky

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
