## Circular Linked List

```java

public class Program {
    static class Node {
        int number;
        Node next;

        public Node(int number) {
            this.number = number;
            next = null;
        }
    }

    public static void main(  ) {
        Node head = new Node(10);
        head.next = new Node(20);
        head.next.next = new Node(30);
        head.next.next.next = new Node(40);
        head.next.next.next.next = head;

        System.out.println("Printing CLL");
        printCLL(head);

        System.out.println("Insert Head");
        head = insertHead(0, head);
        printCLL(head);

        System.out.println("Insert tail");
        head = insertTail(50, head);
        printCLL(head);

        System.out.println("delete head");
        head = deleteHead(head);
        printCLL(head);

        System.out.println("delete kth node");
        head = deleteKthNode(3, head);
        printCLL(head);

    }

    public static void printCLL(Node head) {
        Node ptr = head;

        if (head == null) {
            return;
        }

        // DESIGN
        do {
            System.out.print(ptr.number + " ");
            ptr = ptr.next;
        } while (ptr != head);
        System.out.println();
    }

    public static Node insertHead(int number, Node head) {
        Node temp = new Node(number);

        if (head == null) {
            temp.next = temp;
            return temp;
        }

        temp.next = head.next;
        head.next = temp;

        int t = head.number;
        head.number = temp.number;
        temp.number = t;
        return head;

    }

    public static Node insertTail(int number, Node head) {

        Node temp = new Node(number);

        if (head == null) {
            temp.next = temp;
            return temp;
        }

        temp.next = head.next;
        head.next = temp;

        int t = temp.number;
        temp.number = head.number;
        head.number = t;
        return temp;

    }

    public static Node deleteHead(Node head) {
        if (head == null || head.next == head) {
            return null;
        }

        int t = head.next.number;
        head.next = head.next.next;
        head.number = t;

        return head;

    }

    public static Node deleteKthNode(int pos, Node head) {
        if (pos == 1) {
            return deleteHead(head);
        }

        Node ptr = head;

        for (int i = 0; i < pos - 2; i++) {
            ptr = ptr.next;
        }

        ptr.next = ptr.next.next;
        return head;

    }
}
```

## Circular Doubly LinkedList
```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node {
    int data;
    Node prev;
    Node next;

    Node(int d) {
        data = d;
        prev = null;
        next = null;
    }
}

class Program {

    public static void main ( String[] args ) {
        Node head = new Node(10);
        Node temp1 = new Node(20);
        Node temp2 = new Node(30);
        head.next = temp1;
        temp1.next = temp2;
        temp2.next = head;
        temp2.prev = temp1;
        temp1.prev = head;
        head.prev = temp2;
        head = insertAtHead(head, 5);
        printlist(head);

    }

    public static void printlist(Node head) {
        if (head == null) return;
        Node r = head;
        do {
            System.out.print(r.data + " ");
            r = r.next;
        } while (r != head);
    }

    static Node insertAtHead(Node head, int x) {
        Node temp = new Node(x);
        if (head == null) {
            temp.next = temp;
            temp.prev = temp;
            return temp;
        }
        temp.prev = head.prev;
        temp.next = head;
        head.prev.next = temp;
        head.prev = temp;
        return temp;
    }
} 
```