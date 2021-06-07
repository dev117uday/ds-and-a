---
description: lonely
---

# Singly LinkedList

## Insert into sorted Linkedlist

```java
public class Program {

    static class Node {
        int number;
        Node next;

        public Node(int number) {
            this.number = number;
            this.next = null;
        }
    }

    public static void main(String[] args) {
        Node first = new Node(10);
        first.next = new Node(20);
        first.next.next = new Node(30);
        first.next.next.next = new Node(40);

        Node head = first;

        System.out.println("sorted insert");
        head = sortedInsert(13, head);
        printLL(head);

    }

    public static void printLL(Node head) {
        Node ptr = head;

        do {
            System.out.print(ptr.number + " ");
            ptr = ptr.next;
        } while (ptr != null);

        System.out.println();
    }

    public static Node sortedInsert(int number, Node head) {

        Node temp = new Node(number);

        if (head == null) {
            return temp;
        }

        if (number < head.number) {
            temp.next = head;
            return temp;
        }

        Node curr = head;
        while (curr.next != null && curr.next.number < number) {
            curr = curr.next;
        }

        temp.next = curr.next;
        curr.next = temp;
        return head;

    }
}
```

## Middle of Linkedlist

```java
class Program {

    static class Node {
        int data;
        Node next;

        Node(int x) {
            data = x;
            next = null;
        }
    }

    public static void main ( String[] args ) {
        Node head = new Node(10);
        head.next = new Node(20);
        head.next.next = new Node(30);
        head.next.next.next = new Node(40);
        head.next.next.next.next = new Node(50);
        printlist(head);
        System.out.print("Position of element in Linked List: ");
        printMiddle(head);

    }

    static void printMiddle(Node head) {
        if (head == null) return;
        Node slow = head, fast = head;
        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        System.out.print(slow.data);
    }

    public static void printlist(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }
}
```

## Reverse a LinkedList Iteratively \( recursive is better \)

```java
public class Program {

    static class Node {
        int data;
        Node next;

        Node(int x) {
            data = x;
            next = null;
        }
    }

    public static void main(String[] args ) {
        Node head = new Node(10);
        head.next = new Node(20);
        head.next.next = new Node(30);
        head.next.next.next = new Node(40);
        head.next.next.next.next = new Node(50);

        System.out.print("Position of element in Linked List: ");
        head = reverseLL(head);
        printlist(head);

    }

    static Node reverseLL(Node head) {
        if(head == null || head.next == null) {
            return head;
        }

        Node prev = null;
        Node curr = head;

        while(curr != null) {
            Node next = curr.next;
            curr.next = prev;
            prev = curr;
            curr = next;
        }
        return prev;
    }

    public static void printlist(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }
}
```

## Delete duplicate Item

```java
public class Main {
    static class Node 
    {
        int number;
        Node next;

        public Node(int number)
        {
            this.number = number;
            this.next = null;
        }
    }

    public static void main(String[] args)
    {

        Node head = new Node(0);
        head.next = new Node(10);
        head.next.next = new Node(10);
        head.next.next.next = new Node(30);
        head.next.next.next.next = new Node(30);

        System.out.println("Printing : ");
        printLL(head);

        System.out.println("Deleting : ");
        deleteDLL(head);
        printLL(head);

    }

    static void printLL(Node head) {
        Node ptr = head;
        while(ptr != null) {
            System.out.print(ptr.number+" ");
            ptr = ptr.next;
        }
        System.out.println();
    }

    static void deleteDLL(Node head) {
        Node ptr = head;
        while(ptr != null && ptr.next != null) {
            if (ptr.number == ptr.next.number) {
                ptr.next = ptr.next.next;
            } else {
                ptr = ptr.next;
            }            
        }
    }

}
```

## Reverse a linkedlist recursively

```java
public class Main {
    static class Node {
        int number;
        Node next;

        public Node(int number) {
            this.number = number;
            this.next = null;
        }
    }

    public static void main(String[] args) {
        Node head = new Node(0);
        head.next = new Node(10);
        head.next.next = new Node(20);
        head.next.next.next = new Node(30);

        head = reverseLL(head, null);
        printLL(head);
    }

    public static Node reverseLL(Node curr, Node prev) {
        if (curr == null) {
            return prev;
        }

        Node next = curr.next;
        curr.next = prev;

        return reverseLL(next, curr);
    }

    public static void printLL(Node head) {
        Node ptr = head;
        while (ptr != null) {
            System.out.print(ptr.number + " ");
            ptr = ptr.next;
        }
    }

}
```

## Floyd Detection Algorithm

```java
public class Main {
    static class Node {
        int data;
        Node next;

        Node(int x) {
            data = x;
            next = null;
        }
    }

    public static void main(String args[]) {
        Node head = new Node(15);
        head.next = new Node(10);
        head.next.next = new Node(12);
        head.next.next.next = new Node(20);
        head.next.next.next.next = head.next;
        if (isLoop(head))
            System.out.print("Loop found");
        else
            System.out.print("No Loop");
    }

    static boolean isLoop(Node head) {
        Node slow_p = head, fast_p = head;

        while (fast_p != null && fast_p.next != null) {
            slow_p = slow_p.next;
            fast_p = fast_p.next.next;
            if (slow_p == fast_p) {
                return true;
            }
        }
        return false;
    }

    public static void printlist(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }
}
```

## detect and remove the loop in linkedlist

```java
public class Main {
    static class Node {
        int data;
        Node next;

        Node(int x) {
            data = x;
            next = null;
        }
    }

    public static void main(String args[]) {
        Node head = new Node(15);
        head.next = new Node(10);
        head.next.next = new Node(12);
        head.next.next.next = new Node(20);
        head.next.next.next.next = head.next;
        if (isLoop(head))
            System.out.print("Loop found");
        else
            System.out.print("No Loop");
    }

    static boolean isLoop(Node head) {
        Node slow_p = head, fast_p = head;

        while (fast_p != null && fast_p.next != null) {
            slow_p = slow_p.next;
            fast_p = fast_p.next.next;
            if (slow_p == fast_p) {
                return true;
            }
        }
        return false;
    }

    public static void printlist(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }
}
```

## Delete node with only pointer given to it

```java
class Main {

    static class Node {
        int data;
        Node next;

        Node(int x) {
            data = x;
            next = null;
        }
    }

    public static void main(String args[]) {
        Node head = new Node(10);
        head.next = new Node(20);
        Node ptr = new Node(30);
        head.next.next = ptr;
        head.next.next.next = new Node(40);
        head.next.next.next.next = new Node(25);
        printlist(head);
        deleteNode(ptr);
        printlist(head);
    }

    static void deleteNode(Node ptr) {
        Node temp = ptr.next;
        ptr.data = temp.data;
        ptr.next = temp.next;
    }

    public static void printlist(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }
}
```

## Segerate even & odd nodes in linkedlist

```java
public class Main {

    static class Node {
        int data;
        Node next;

        Node(int x) {
            data = x;
            next = null;
        }
    }

    public static void main(String args[]) {
        Node head = new Node(17);
        head.next = new Node(15);
        head.next.next = new Node(8);
        head.next.next.next = new Node(12);
        head.next.next.next.next = new Node(10);
        head.next.next.next.next.next = new Node(5);
        head.next.next.next.next.next.next = new Node(4);
        printlist(head);
        head = segregate(head);
        printlist(head);

    }

    static Node segregate(Node head) {
        Node eS = null, eE = null, oS = null, oE = null;
        for (Node curr = head; curr != null; curr = curr.next) {
            int x = curr.data;
            if (x % 2 == 0) {
                if (eS == null) {
                    eS = curr;
                    eE = eS;
                } else {
                    eE.next = curr;
                    eE = eE.next;
                }
            } else {
                if (oS == null) {
                    oS = curr;
                    oE = oS;
                } else {
                    oE.next = curr;
                    oE = oE.next;
                }
            }
        }
        if (oS == null || eS == null)
            return head;
        eE.next = oS;
        oE.next = null;
        return eS;
    }

    public static void printlist(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }
}
```

## Intersection of two linkedlist

```java
class Main {

    static Node headA, headB;

    static class Node {

        int data;
        Node next;

        Node(int d) {
            data = d;
            next = null;
        }
    }

    int getNode() {
        int c1 = getCount(headA);
        int c2 = getCount(headB);
        int d;

        if (c1 > c2) {
            d = c1 - c2;
            return _getIntesectionNode(d, headA, headB);
        } else {
            d = c2 - c1;
            return _getIntesectionNode(d, headB, headA);
        }
    }

    int _getIntesectionNode(int d, Node node1, Node node2) {
        int i;
        Node current1 = node1;
        Node current2 = node2;
        for (i = 0; i < d; i++) {
            if (current1 == null) {
                return -1;
            }
            current1 = current1.next;
        }
        while (current1 != null && current2 != null) {
            if (current1.data == current2.data) {
                return current1.data;
            }
            current1 = current1.next;
            current2 = current2.next;
        }

        return -1;
    }

    int getCount(Node node) {
        Node current = node;
        int count = 0;

        while (current != null) {
            count++;
            current = current.next;
        }

        return count;
    }

    public static void main(String[] args) {
        Main list = new Main();

        list.headA = new Node(3);
        list.headA.next = new Node(6);
        list.headA.next.next = new Node(9);
        list.headA.next.next.next = new Node(15);
        list.headA.next.next.next.next = new Node(30);

        list.headB = new Node(10);
        list.headB.next = new Node(15);
        list.headB.next.next = new Node(30);

        System.out.println(list.getNode());
    }
}
```

## Pairwise swap in linkedlist

```java
class Main {
    static class Node {
        int data;
        Node next;

        Node(int x) {
            data = x;
            next = null;
        }
    }

    public static void main(String args[]) {
        Node head = new Node(1);
        head.next = new Node(2);
        head.next.next = new Node(3);
        head.next.next.next = new Node(4);
        head.next.next.next.next = new Node(5);
        printlist(head);
        head = pairwiseSwap(head);
        printlist(head);

    }

    static Node pairwiseSwap(Node head) {
        if (head == null || head.next == null)
            return head;
        Node curr = head.next.next;
        Node prev = head;
        head = head.next;
        head.next = prev;
        while (curr != null && curr.next != null) {
            prev.next = curr.next;
            prev = curr;
            Node next = curr.next.next;
            curr.next.next = curr;
            curr = next;
        }
        prev.next = curr;
        return head;
    }

    public static void printlist(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }
}
```

## Clone a linked list using a random pointer

```java
import java.util.HashMap;

class Main {

    static class Node {
        int data;
        Node next, random;

        Node(int x) {
            data = x;
            next = random = null;
        }
    }

    public static void print(Node start) {
        Node ptr = start;
        while (ptr != null) {
            System.out.println("Data = " + ptr.data + ", Random  = " + ptr.random.data);
            ptr = ptr.next;
        }
    }

    public static Node clone(Node head) {
        HashMap<Node, Node> hm = new HashMap<Node, Node>();
        for (Node curr = head; curr != null; curr = curr.next)
            hm.put(curr, new Node(curr.data));

        for (Node curr = head; curr != null; curr = curr.next) {
            Node cloneCurr = hm.get(curr);
            cloneCurr.next = hm.get(curr.next);
            cloneCurr.random = hm.get(curr.random);
        }
        Node head2 = hm.get(head);

        return head2;
    }

    public static void main(String[] args) {
        Node head = new Node(10);
        head.next = new Node(5);
        head.next.next = new Node(20);
        head.next.next.next = new Node(15);
        head.next.next.next.next = new Node(20);

        head.random = head.next.next;
        head.next.random = head.next.next.next;
        head.next.next.random = head;
        head.next.next.next.random = head.next.next;
        head.next.next.next.next.random = head.next.next.next;

        System.out.print("Original list : \n");
        print(head);

        System.out.print("\nCloned list : \n");
        Node cloned_list = clone(head);
        print(cloned_list);
    }
}
```

## Clone linkedlist using random pointer without hashing

```java
public class Main {
    static class Node {
        int data;
        Node next, random;

        Node(int x) {
            data = x;
            next = random = null;
        }
    }

    public static void print(Node start) {
        Node ptr = start;
        while (ptr != null) {
            System.out.println("Data = " + ptr.data + ", Random  = " + ptr.random.data);
            ptr = ptr.next;
        }
    }

    public static Node clone(Node head) {
        Node next, temp;
        for (Node curr = head; curr != null;) {
            next = curr.next;
            curr.next = new Node(curr.data);
            curr.next.next = next;
            curr = next;
        }
        for (Node curr = head; curr != null; curr = curr.next.next) {
            curr.next.random = (curr.random != null) ? (curr.random.next) : null;
        }

        Node original = head, copy = head.next;

        temp = copy;

        while (original != null && copy != null) {
            original.next = original.next != null ? original.next.next : original.next;

            copy.next = copy.next != null ? copy.next.next : copy.next;
            original = original.next;
            copy = copy.next;
        }

        return temp;
    }

    public static void main(String[] args) {
        Node head = new Node(10);
        head.next = new Node(5);
        head.next.next = new Node(20);
        head.next.next.next = new Node(15);
        head.next.next.next.next = new Node(20);

        head.random = head.next.next;
        head.next.random = head.next.next.next;
        head.next.next.random = head;
        head.next.next.next.random = head.next.next;
        head.next.next.next.next.random = head.next.next.next;

        System.out.print("Original list : \n");
        print(head);

        System.out.print("\nCloned list : \n");
        Node cloned_list = clone(head);
        print(cloned_list);
    }
}
```

## LRU \( least recently used \) Cache Design

```java
import java.util.*;
import java.io.*;
import java.lang.*;
import java.util.*; 

class Node { 
    int key; 
    int value; 
    Node pre; 
    Node next; 

    public Node(int key, int value) 
    { 
        this.key = key; 
        this.value = value; 
    } 
} 

class LRUCache { 
    private HashMap<Integer, Node> map; 
    private int capacity, count; 
    private Node head, tail; 

    public LRUCache(int capacity) 
    { 
        this.capacity = capacity; 
        map = new HashMap<>(); 
        head = new Node(0, 0); 
        tail = new Node(0, 0); 
        head.next = tail; 
        tail.pre = head; 
        head.pre = null; 
        tail.next = null; 
        count = 0; 
    } 

    public void deleteNode(Node node) 
    { 
        node.pre.next = node.next; 
        node.next.pre = node.pre; 
    } 

    public void addToHead(Node node) 
    { 
        node.next = head.next; 
        node.next.pre = node; 
        node.pre = head; 
        head.next = node; 
    } 

    public int get(int key) 
    { 
        if (map.get(key) != null) { 
            Node node = map.get(key); 
            int result = node.value; 
            deleteNode(node); 
            addToHead(node); 
            System.out.println("Got the value : " + 
                result + " for the key: " + key); 
            return result; 
        } 
        System.out.println("Did not get any value" + 
                            " for the key: " + key); 
        return -1; 
    } 

    public void set(int key, int value) 
    { 
        System.out.println("Going to set the (key, "+ 
            "value) : (" + key + ", " + value + ")"); 
        if (map.get(key) != null) { 
            Node node = map.get(key); 
            node.value = value; 
            deleteNode(node); 
            addToHead(node); 
        } 
        else { 
            Node node = new Node(key, value); 
            map.put(key, node); 
            if (count < capacity) { 
                count++; 
                addToHead(node); 
            } 
            else { 
                map.remove(tail.pre.key); 
                deleteNode(tail.pre); 
                addToHead(node); 
            } 
        } 
    } 
} 

public class TestLRUCache { 
    public static void main(String[] args) 
    { 

        LRUCache cache = new LRUCache(2); 

        // it will store a key (1) with value 
        // 10 in the cache. 
        cache.set(1, 10); 

        // it will store a key (2) with value 20 in the cache. 
        cache.set(2, 20); 
        System.out.println("Value for the key: 1 is " + cache.get(1)); // returns 10 

        // removing key 2 and store a key (3) with value 30 in the cache. 
        cache.set(3, 30); 

        System.out.println("Value for the key: 2 is " + 
                cache.get(2)); // returns -1 (not found) 

        // removing key 1 and store a key (4) with value 40 in the cache. 
        cache.set(4, 40); 
        System.out.println("Value for the key: 1 is " + 
            cache.get(1)); // returns -1 (not found) 
        System.out.println("Value for the key: 3 is " + 
                        cache.get(3)); // returns 30 
        System.out.println("Value for the key: 4 is " + 
                        cache.get(4)); // return 40 
    } 
}
```

## Merge two sorted linked lists

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node {
    int data;
    Node next;

    Node(int x) {
        data = x;
        next = null;
    }
}

class Test {

    public static void main(String args[]) {
        Node a = new Node(10);
        a.next = new Node(20);
        a.next.next = new Node(30);
        Node b = new Node(5);
        b.next = new Node(35);
        printlist(sortedMerge(a, b));

    }

    static Node sortedMerge(Node a, Node b) {
        if (a == null)
            return b;
        if (b == null)
            return a;
        Node head = null, tail = null;
        if (a.data <= b.data) {
            head = tail = a;
            a = a.next;
        } else {
            head = tail = b;
            b = b.next;
        }
        while (a != null && b != null) {
            if (a.data <= b.data) {
                tail.next = a;
                tail = a;
                a = a.next;
            } else {
                tail.next = b;
                tail = b;
                b = b.next;
            }
        }
        if (a == null) {
            tail.next = b;
        } else {
            tail.next = a;
        }
        return head;
    }

    public static void printlist(Node head) {
        Node curr = head;
        while (curr != null) {
            System.out.print(curr.data + " ");
            curr = curr.next;
        }
        System.out.println();
    }
}
```

## Palindrome linkedlist

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node {
    char data;
    Node next;

    Node(char x) {
        data = x;
        next = null;
    }
}

class Test {

    public static void main(String args[]) {
        Node head = new Node('g');
        head.next = new Node('f');
        head.next.next = new Node('g');
        if (isPalindrome(head))
            System.out.print("Yes");
        else
            System.out.print("No");

    }

    static Node reverseList(Node head) {
        if (head == null || head.next == null)
            return head;
        Node rest_head = reverseList(head.next);
        Node rest_tail = head.next;
        rest_tail.next = head;
        head.next = null;
        return rest_head;
    }

    static boolean isPalindrome(Node head) {
        if (head == null)
            return true;
        Node slow = head, fast = head;
        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }
        Node rev = reverseList(slow.next);
        Node curr = head;
        while (rev != null) {
            if (rev.data != curr.data)
                return false;
            rev = rev.next;
            curr = curr.next;
        }
        return true;
    }
}
```

