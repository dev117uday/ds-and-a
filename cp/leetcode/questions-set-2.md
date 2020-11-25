---
description: Leetcode solutions set 2
---

# Questions \(Set 2\)

### Remove Nth Node From End of List

```text
func removeNthFromEnd(head *ListNode, n int) *ListNode {
    if n == 1 {
        if head.Next == nil {
            head = nil
            return head
        }
    }

    i:=0
    ptr := head 
    for ptr != nil {
        i++
        if n == 1 && ptr.Next.Next == nil {
            ptr.Next = nil
            return head
        }

        ptr = ptr.Next
    }
    if i == n {
        head = head.Next
        return head
    }
    n = i - n
    i = 1
    ptr = head 
    for ptr != nil {
        if i == n {
            ptr.Next = ptr.Next.Next
            return head
        }
        i++
        ptr = ptr.Next
    }
    return nil
    
}
```

### Design Linkedlist Golang

```text
type Node struct {
	val  int
	next *Node
}
type MyLinkedList struct {
	length int
	head   *Node
	tail   *Node
}

/** Initialize your data structure here. */
func Constructor() MyLinkedList {
	return MyLinkedList{0, nil, nil}
}

/** Get the value of the index-th node in the linked list. If the index is invalid, return -1. */
func (this *MyLinkedList) Get(index int) int {
	if index < 0 {
		return -1
	}
	i := 0
	ptr := this.head
	for ptr != nil {
		if i == index {
			return ptr.val
		}
		ptr = ptr.next
		i++
	}
	return -1
}

/** Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list. */
func (this *MyLinkedList) AddAtHead(val int) {
	newNode := Node{val, nil}

	if this.head == nil {
		newNode.next = nil
		this.head = &newNode
		this.tail = &newNode
	} else {
		newNode.next = this.head
		this.head = &newNode
	}
	this.length++
}

/** Append a node of value val to the last element of the linked list. */
func (this *MyLinkedList) AddAtTail(val int) {
	newNode := Node{val, nil}

	if this.head == nil {
		newNode.next = nil
		this.head = &newNode
		this.tail = &newNode
	} else {
		newNode.next = nil
		this.tail.next = &newNode
		this.tail = &newNode
	}
	this.length++
}

/** Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted. */
func (this *MyLinkedList) AddAtIndex(index int, val int) {
	if index == 0 {
		this.AddAtHead(val)
	}
	ptr := this.head
	i := 0
	for ptr != nil {
		if ptr.next == nil {
			this.AddAtTail(val)
			return
		}
		if i == index-1 {
			newNode := Node{val, nil}
			newNode.next = ptr.next
			ptr.next = &newNode
			this.length++
			return
		}
		ptr = ptr.next
		i++
	}

}

/** Delete the index-th node in the linked list, if the index is valid. */
func (this *MyLinkedList) DeleteAtIndex(index int) {
	if index < 0 {
		return
	}
	if index == 0 {
		this.head = this.head.next
		this.length--
		return
	} else if index > this.length {
		return
	} else {
		ptr := this.head
		i := 0
		for ptr != nil {
			if i == index-1 {
				if ptr.next != nil {
					if ptr.next.next == nil {
						ptr.next = nil
						this.tail = ptr
						this.length--
						return
					} else {
						ptr.next = ptr.next.next
						this.length--
						return
					}
				} else {
					return
				}
			}
			ptr = ptr.next
			i++
		}
	}
}
```

