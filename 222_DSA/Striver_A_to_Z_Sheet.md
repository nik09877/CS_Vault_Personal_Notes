# Linked List
## ADVICE : Always Check For NULL
### [237. Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/)
- We are given a node not Head
- copy next node value and point to next to next node
- TC O(1)
- SC O(1)
- 
### [Count nodes of linked list](https://www.codingninjas.com/studio/problems/count-nodes-of-linked-list_5884?utm_source=striver&utm_medium=website&utm_campaign=a_zcoursetuf)
- use fast, slow pointer
-  Initially `fast = slow = head;`
- TC O(N)
- SC O(N)
- 
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
