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
### [Reverse Nodes in k-Group - LeetCode](https://leetcode.com/problems/reverse-nodes-in-k-group/)

### [Rotate List - LeetCode](https://leetcode.com/problems/rotate-list/description/)

### [Flatten A Linked List - Coding Ninjas](https://www.codingninjas.com/studio/problems/flatten-a-linked-list_1112655?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)

### [Copy List with Random Pointer - LeetCode](https://leetcode.com/problems/copy-list-with-random-pointer/)