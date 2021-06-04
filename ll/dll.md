# Doubly LinkedList

```java
public class Program {

    static class Node {
        int number;
        Node next;
        Node prev;

        public Node(int number) {
            this.number = number;
            this.next = null;
            this.prev = null;
        }
    }

    public static void main(  ) {

        Node head;
        Node first = new Node(10);
        Node second = new Node(20);
        Node third = new Node(30);
        Node fourth = new Node(40);

        first.next = second;
        first.prev = null;
        second.next = third;
        second.prev = first;
        third.prev = second;
        third.next = fourth;
        fourth.prev = third;
        fourth.next = null;

        System.out.println("Inserting at the beginning");
        head = insertAtTheBegin(0, first);
        printLL(head);

        System.out.println("Inserting at the End");
        head = insertAtTheEnd(50, head);
        printLL(head);

        System.out.println("Delete Head");
        head = deleteHeadDLL(head);
        printLL(head);

        System.out.println("Delete Last Node ");
        head = deleteLastHead(head);
        printLL(head);

        System.out.println("reversing a DLL");
        Node newHead = reverseDLL(head);
        printLL(newHead);
    }

    public static void printLL(Node node) {

        if (node == null) {
            System.out.println();
            return;
        }

        System.out.print(node.number + " ");
        printLL(node.next);

    }

    public static Node insertAtTheBegin(int number, Node head) {

        if (head == null) {
            return new Node(number);
        }

        Node temp = new Node(number);
        head.prev = temp;
        temp.next = head;
        return temp;
    }

    public static Node insertAtTheEnd(int number, Node head) {
        if (head == null) {
            return new Node(number);
        }

        Node ptr = head;

        // DESIGN
        while (ptr.next != null)
            ptr = ptr.next;

        Node temp = new Node(number);
        ptr.next = temp;
        temp.prev = ptr;
        return head;
    }

    public static Node reverseDLL(Node head) {
        if (head == null || head.next == null) {
            return head;
        }

        Node prev = null;
        Node curr = head;

        while (curr != null) {
            prev = curr.prev;
            curr.prev = curr.next;
            curr.next = prev;
            curr = curr.prev;
        }
        return prev.prev;

    }

    public static Node deleteHeadDLL(Node head) {
        if (head == null) {
            return head;
        }

        if (head.next == null) {
            return null;
        }

        head = head.next;
        head.prev = null;
        return head;

    }

    public static Node deleteLastHead(Node head) {
        if (head == null) {
            return head;
        }
        if (head.next == null) {
            return null;
        }

        Node ptr = head;
        while (ptr.next.next != null)
            ptr = ptr.next;

        ptr.next = null;
        return head;
    }

}
```

