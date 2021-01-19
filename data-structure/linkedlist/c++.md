---
description: Linkedlist
---

# C++

## circular-linkedlist.cpp

```cpp
#include <iostream>

using namespace std;

struct CircularLinkedList {
    int number;
    CircularLinkedList *next;
};

class ImplCirLL {
    CircularLinkedList *head = nullptr;
    CircularLinkedList *guide = nullptr;
public :
    void insert(int number ){
        auto *ptr = new CircularLinkedList();
        ptr->number = number;
        if (this->head == nullptr)    {
            this->head = ptr;
            guide = ptr;
            ptr->next = this->head;
        } else {
            guide->next = ptr;
            guide = ptr;
            ptr->next = this->head;
        }
    }
    void display(){
        CircularLinkedList *ptr = this->head;
        cout << ptr->number << " ";
        ptr = ptr->next;
        while (ptr != this->head){
            cout << ptr->number << " ";
            ptr = ptr->next;
        }
    }
};

int main(){
    ImplCirLL cirLL;
    cirLL.insert(0);
    cirLL.insert(1);
    cirLL.insert(2);
    cirLL.display();
    cirLL.insert(0);
    cirLL.insert(1);
    cirLL.insert(2);
    cirLL.display();
}
```

## double-linked-list.cpp

```cpp
#include <iostream>

using namespace std;

struct DoubleLinkedList
{
    int number;
    DoubleLinkedList *next;
    DoubleLinkedList *prev;
};

class ImplDoubleLL
{
    DoubleLinkedList *head = nullptr;
    DoubleLinkedList *guide = nullptr;

public:
    void insert(int number)
    {
        auto *ptr = new DoubleLinkedList();
        ptr->number = number;
        if (this->head == nullptr)
        {
            ptr->prev = nullptr;
            this->head = ptr;
            ptr->next = nullptr;
            guide = ptr;
        }
        else
        {
            ptr->next = nullptr;
            guide->next = ptr;
            ptr->prev = guide;
            guide = ptr;
        }
    }

    void display()
    {
        DoubleLinkedList *ptr = this->head;
        while (ptr != nullptr)
        {
            cout << ptr->number << " ";
            ptr = ptr->next;
        }
    }

    void display_reverse()
    {
        DoubleLinkedList *ptr = guide;
        while (ptr != nullptr)
        {
            cout << ptr->number << " ";
            ptr = ptr->prev;
        }
    }
};

int main()
{
    ImplDoubleLL DoubleLL;
    DoubleLL.insert(0);
    DoubleLL.insert(1);
    DoubleLL.insert(2);
    DoubleLL.insert(3);
    DoubleLL.display();
    cout << " | ";
    DoubleLL.display_reverse();
    cout << "\n";
}
```

## linkedlist.cpp

```cpp
#include <iostream>

using namespace std;

struct LinkedList
{
    int number;
    LinkedList *next;
};

class ImplLL
{
    LinkedList *head = nullptr;
    LinkedList *guide = nullptr;

public:
    void insert(int number)
    {
        auto *ptr = new LinkedList();
        ptr->number = number;
        ptr->next = nullptr;

        if (head == nullptr)
        {
            head = ptr;
            guide = ptr;
        }
        else
        {
            guide->next = ptr;
            guide = ptr;
        }
    }
    void display()
    {
        LinkedList *ptr = head;

        while (ptr != nullptr)
        {
            cout << ptr->number << " ";
            ptr = ptr->next;
        }
    }
};

int main()
{
    ImplLL LinkedL;
    LinkedL.insert(0);
    LinkedL.insert(1);
    LinkedL.insert(2);
    LinkedL.display();
}
```

