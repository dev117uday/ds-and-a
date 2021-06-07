---
description: Simple
---

# LinkedList

## Linked List Implementation

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

        Node head;
        Node first = new Node(10);
        Node second = new Node(20);
        Node third = new Node(30);
        Node fourth = new Node(40);

        first.next = second;
        second.next = third;
        third.next = fourth;

        System.out.println("Iterative Printing");
        printLinkedList(first);

        System.out.println("Recursive Printing");
        printLinkedLRecursive(first);

        System.out.println("Inserting head");
        head = insertHeadLL(0, first);
        printLinkedLRecursive(head);

        System.out.println("Inserting at end");
        head = insertNodeEndLL(50, head);
        printLinkedLRecursive(head);

        System.out.println("Deleting Head node");
        head = deleteHeadNodeLL(head);
        printLinkedList(head);

        System.out.println("Delete Last node");
        head = deleteLastNodeLL(head);
        printLinkedLRecursive(head);

        System.out.println("Insert data at postion");
        head = insertDataAtPos(4, 25, head);
        printLinkedLRecursive(head);

        System.out.println("Find Data iter  : " + searchInLLIter(30, head));
        System.out.println("Find Data recur : " + searchInLLRec(60, 1, head));

    }

    public static void printLinkedList(Node curr) {
        while (curr != null) {
            System.out.print(curr.number + " ");
            curr = curr.next;
        }
        System.out.println();
    }

    public static void printLinkedLRecursive(Node curr) {
        if (curr == null) {
            System.out.println();
            return;
        }
        System.out.print(curr.number + " ");
        printLinkedLRecursive(curr.next);
    }

    public static Node insertHeadLL(int number, Node currHead) {
        Node newNode = new Node(number);
        newNode.next = currHead;
        return newNode;
    }

    public static Node insertNodeEndLL(int number, Node head) {
        Node ptr = head;
        if (head == null) {
            return insertHeadLL(number, null);
        }

        // DESIGN
        while (ptr.next != null)
            ptr = ptr.next;

        ptr.next = new Node(number);
        return head;

    }

    public static Node deleteHeadNodeLL(Node head) {
        if (head == null) {
            return null;
        }
        return head.next;
    }

    public static Node deleteLastNodeLL(Node head) {
        if (head == null) {
            return null;
        }

        if (head.next == null) {
            return null;
        }

        Node ptr = head;

        // DESIGN
        while (ptr.next.next != null)
            ptr = ptr.next;

        ptr.next = null;
        return head;
    }

    public static Node insertDataAtPos(int position, int number, Node head) {
        if (position == 1) {
            return insertHeadLL(number, head);
        }

        // *** DESIGN ***
        Node ptr = head;
        for (int i = 1; i < position - 1 && ptr != null; i++) {
            ptr = ptr.next;
        }

        if (ptr == null) {
            return head;
        }

        Node temp = new Node(number);
        temp.next = ptr.next;
        ptr.next = temp;
        return head;

    }

    public static int searchInLLIter(int number, Node head) {
        Node ptr = head;
        int count = 1;
        while (ptr != null) {
            if (ptr.number == number) {
                return count;
            }
            ptr = ptr.next;
            count++;
        }
        return -1;
    }

    public static int searchInLLRec(int number, int index, Node head) {
        if (head == null) {
            return -1;
        }
        if (head.number == number) {
            return index;
        }
        return searchInLLRec(number, index + 1, head.next);
    }
}
```

