---
description: Linkedlist
---

# Golang

### circularlinkedlist.go

```go
package main

import "fmt"

type CircularLinkedList struct {
    number int
    next *CircularLinkedList
}

type ImpleCircularLL struct {
    head *CircularLinkedList
    guide *CircularLinkedList
}

func (icl *ImpleCircularLL) insert(number int) {
    var ptr = CircularLinkedList{}
    ptr.number = number
    if icl.head == nil {
        icl.head = &ptr
        icl.guide = &ptr
        ptr.next = icl.head
    } else {
        icl.guide.next = &ptr
        ptr.next = icl.head
        icl.guide = &ptr
    }
}
func (icl *ImpleCircularLL) display(){
    var ptr = icl.head
    fmt.Println(ptr.number)
    ptr = ptr.next
    if ptr == nil {
        return
    }
    for ptr != icl.head {
        fmt.Println(ptr.number)
        ptr = ptr.next
    }
}

func main() {
    var cirLL = ImpleCircularLL{nil,nil}
    cirLL.insert(0)
    cirLL.insert(1)
    cirLL.insert(2)
    cirLL.insert(3)
    cirLL.display()
}
```

### doublylinkedlist.go

```go
package main

import "fmt"

type DoubleLinkedList struct {
    number int
    next *DoubleLinkedList
    prev *DoubleLinkedList
}

type ImplDoubleLL struct {
    head *DoubleLinkedList
    guide * DoubleLinkedList
}

func (idl *ImplDoubleLL) insert(number int) {
    var ptr = DoubleLinkedList{}
    ptr.number = number
    ptr.next = nil
    if idl.head == nil {
        idl.head = &ptr
        idl.guide = &ptr
        ptr.prev = nil
    } else {
        idl.guide.next = &ptr
        ptr.prev = idl.guide
        idl.guide = &ptr
    }
}

func (idl *ImplDoubleLL) display(){

    var ptr *DoubleLinkedList = idl.head
    for ptr != nil {
        fmt.Println(ptr.number)
        ptr = ptr.next
    }

}

func (idl *ImplDoubleLL) display_reverse() {

    var ptr *DoubleLinkedList = idl.guide
    for ptr!=nil{
        fmt.Println(ptr.number)
        ptr = ptr.prev
    }

}

func main() {
    var dll = ImplDoubleLL{nil,nil}
    dll.insert(0)
    dll.insert(1)
    dll.insert(2)
    dll.insert(3)
    dll.display()
    fmt.Println("")
    dll.display_reverse()
}
```

### falling\_linkedlist.go

```go
package main

import "fmt"

type LinkedList struct {
    number int
    next *LinkedList
}

type List struct {
    head *LinkedList
    guide *LinkedList
}

func (L *List) insert (number int) {
    var ptr = LinkedList{}
    ptr.number = number
    ptr.next = L.head
    L.head = &ptr
}

func (L *List) display(){
    var ptr *LinkedList = L.head
    for ptr != nil {
        fmt.Println(ptr.number)
        ptr = ptr.next
    }
}

func main(){
    var numberFallingList = List{nil,nil}
    numberFallingList.insert(0)
    numberFallingList.insert(1)
    numberFallingList.insert(2)
    numberFallingList.insert(3)
    numberFallingList.display()
}
```

### linkedlist.go

```go
package main

import "fmt"

type LinkedList struct {
    number int
    next   *LinkedList
}
type List struct {
    head  *LinkedList
    guide *LinkedList
}

func main() {
    var numberList = List{nil, nil}
    numberList.insert(0)
    numberList.insert(1)
    numberList.insert(2)
    numberList.insert(3)
    numberList.insert(4)
    numberList.insertAfter(2, 10)
    numberList.insertAfter(4, 6)
    numberList.attach(-1)
    numberList.attach(-2)
    numberList.insertBefore(6, 7)
    numberList.display()
}

func (L *List) insert(number int) {
    var ptr = LinkedList{}
    ptr.number = number
    ptr.next = nil
    if L.head == nil {
        L.head = &ptr
        L.guide = &ptr
    } else {
        L.guide.next = &ptr
        L.guide = &ptr
    }
}

func (L *List) display() {
    var ptr *LinkedList = L.head
    for ptr != nil {
        fmt.Println(ptr.number)
        ptr = ptr.next
    }
}

func (L *List) insertAfter(number int, toSet int) {
    var ptr *LinkedList = L.head
    for ptr != nil {
        if ptr.number == number {
            if ptr.next != nil {
                var temp = LinkedList{}
                temp.number = toSet
                temp.next = ptr.next
                ptr.next = &temp
                return
            } else {
                L.insert(toSet)
            }
        }
        ptr = ptr.next
    }
}

func (L *List) insertBefore(number int, toSet int) {
    var ptr *LinkedList = L.head
    for ptr != nil {
        if ptr.next == nil {
            fmt.Println("Not Found")
            break
        } else if ptr.next.number == number {
            var newNode = LinkedList{}
            newNode.number = toSet
            newNode.next = ptr.next
            ptr.next = &newNode
            break
        }
        ptr = ptr.next
    }
}

func (L *List) attach(number int) {
    var ptr = LinkedList{}
    ptr.number = number
    ptr.next = L.head
    L.head = &ptr
}
```

### list.go

```go
package linkedlist

type node struct {
    value interface{}
    prev  *node
    next  *node
}

// LinkedList - a doubly linked list implementation
type LinkedList struct {
    head  *node
    tail  *node
    count int
}

func (list *LinkedList) validateIndex(index int) {
    if index < 0 || index >= list.count {
        panic("Index out of range")
    }
}

// New - creates an empty linkedlist
func New() *LinkedList {
    newList := &LinkedList{}
    return newList
}

// Size - returns number of items in list
func (list *LinkedList) Size() int {
    return list.count
}

// PushEnd - adds an item at the end
func (list *LinkedList) PushEnd(value interface{}) {
    new := &node{value: value, prev: list.tail}
    if list.count == 0 {
        list.head = new
    } else {
        list.tail.next = new
    }
    list.tail = new
    list.count++
}

// ValueAt - returns the value of the nth item (starting at 0 for first)
func (list *LinkedList) ValueAt(index int) interface{} {
    list.validateIndex(index)
    tmp := list.head
    for i := 0; i < index; i++ {
        tmp = tmp.next
    }
    return tmp.value
}

// PushFront - adds an item to the front of the list
func (list *LinkedList) PushFront(value interface{}) {
    new := &node{value: value, next: list.head}
    if list.head == nil {
        list.tail = new
    } else {
        list.head.prev = new
    }
    list.head = new
    list.count++
}

// PopEnd - removes end item and returns its value
func (list *LinkedList) PopEnd() interface{} {
    if list.count == 0 {
        panic("pop called on an empty list")
    }
    result := list.tail.value
    list.tail = list.tail.prev
    if list.tail != nil {
        list.tail.next = nil
    } else {
        list.head = nil
    }
    list.count--
    return result
}

// PopFront - remove front item and return its value
func (list *LinkedList) PopFront() interface{} {

    if list.count == 0 {
        panic("pop called on an empty list")
    }
    result := list.head.value
    list.head = list.head.next

    if list.head != nil {
        list.head.prev = nil
    } else {
        list.tail = nil
    }

    list.count--
    return result
}

// Insert - insert value at index
func (list *LinkedList) Insert(index int, value interface{}) {
    if index == list.count {
        list.PushEnd(value)
    } else if index == 0 {
        list.PushFront(value)
    } else {
        list.validateIndex(index)

        curr := list.head
        // TODO choose the closest side to seek
        for index > 0 {
            curr = curr.next
            index--
        }
        // [prev] <->  [curr]  <->  [next]  <-> ...
        //             [new]
        new := &node{value: value, prev: curr.prev, next: curr}

        // aralanın mən də oturum
        curr.prev.next = new
        curr.prev = new
        list.count++
    }

}

// Iterate yields elements as buffered channel
func (list *LinkedList) Iterate() chan interface{} {
    ch := make(chan interface{}, list.count)

    for curr := list.head; curr != nil; curr = curr.next {
        ch <- curr.value
    }
    close(ch)
    return ch
}

// RemoveAt - removes node at given index
func (list *LinkedList) RemoveAt(index int) {
    list.validateIndex(index)
    if index == 0 {
        list.PopFront()
    } else if index == list.count-1 {
        list.PopEnd()
    }
    curr := list.head
    for index > 0 {
        curr = curr.next
        index--
    }
    // əl çəkin mənnən
    curr.prev.next = curr.next
    curr.next.prev = curr.prev
    list.count--
}

// Reverse - reverses the list
func (list *LinkedList) Reverse() {
    if list.count < 2 {
        return
    }
    list.head, list.tail = list.tail, list.head
    for curr := list.head; curr != nil; curr = curr.next {
        curr.prev, curr.next = curr.next, curr.prev
    }
}

// RemoveValue - removes the first occurence
func (list *LinkedList) RemoveValue(value interface{}) bool {
    if list.count == 0 {
        return false
    } else if value == list.head.value {
        list.PopFront()
        return true
    } else if value == list.tail.value {
        list.PopEnd()
        return true
    }

    for curr := list.head.next; curr != nil; curr = curr.next {
        if curr.value == value {
            curr.prev.next = curr.next
            curr.next.prev = curr.prev
            list.count--
            return true
        }
    }
    return false
}
```

