---
description: Garbage
---

# Heap
children elements are smaller/bigger than parent

## Types of Heaps
- Min Heap : Highest priority items assigned the lowest value
- Max Heap : Highest priority items assigned the highest value

## Applications of Heap
- Used to implement HeapSort
- Used to implement PriorityQueue

## Formulae's
- left of element : (2*i+1)
- right of element : (2*i+2)
- parent of element : (i-1)/2

## Binary Heap Implementation (Array)
```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Main {

    public static class MinHeap {
        int arr[];
        int size;
        int capacity;

        MinHeap(int c) {
            size = 0;
            capacity = c;
            arr = new int[c];
        }

        int left(int i) {
            return (2 * i + 1);
        }

        int right(int i) {
            return (2 * i + 2);
        }

        int parent(int i) {
            return (i - 1) / 2;
        }
    }

    public static void main(String args[]) {
        MinHeap h = new MinHeap(11);

    }

} 
```

## Binary Heap Insert (Array) : MinHeap
```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Test {

    public static class MinHeap {
        int arr[];
        int size;
        int capacity;

        MinHeap(int c) {
            size = 0;
            capacity = c;
            arr = new int[c];
        }

        int left(int i) {
            return (2 * i + 1);
        }

        int right(int i) {
            return (2 * i + 2);
        }

        int parent(int i) {
            return (i - 1) / 2;
        }


        public void insert(int x) {
            if (size == capacity) return;
            size++;
            arr[size - 1] = x;

            for (int i = size - 1; i != 0 && arr[parent(i)] > arr[i]; ) {
                int temp = arr[i];
                arr[i] = arr[parent(i)];
                arr[parent(i)] = temp;
                i = parent(i);
            }
        }

    }

    public static void main(String args[]) {
        MinHeap h = new MinHeap(11);
        h.insert(3);
        h.insert(2);
        h.insert(15);
        h.insert(20);
    }

} 
```

## Binary Heap (Heapify and Extract) : MinHeap
**Extract operation is super important**
```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Test {

    public static class MinHeap {
        int arr[];
        int size;
        int capacity;

        MinHeap(int c) {
            size = 0;
            capacity = c;
            arr = new int[c];
        }

        int left(int i) {
            return (2 * i + 1);
        }

        int right(int i) {
            return (2 * i + 2);
        }

        int parent(int i) {
            return (i - 1) / 2;
        }


        public void insert(int x) {
            if (size == capacity) return;
            size++;
            arr[size - 1] = x;

            for (int i = size - 1; i != 0 && arr[parent(i)] > arr[i]; ) {
                int temp = arr[i];
                arr[i] = arr[parent(i)];
                arr[parent(i)] = temp;
                i = parent(i);
            }
        }

        public void minHeapify(int i) {
            int lt = left(i);
            int rt = right(i);
            int smallest = i;
            if (lt < size && arr[lt] < arr[i])
                smallest = lt;
            if (rt < size && arr[rt] < arr[smallest])
                smallest = rt;
            if (smallest != i) {
                int temp = arr[i];
                arr[i] = arr[smallest];
                arr[smallest] = temp;
                minHeapify(smallest);
            }
        }

        public int extractMin() {
            if (size <= 0)
                return Integer.MAX_VALUE;
            if (size == 1) {
                size--;
                return arr[0];
            }
            int temp = arr[0];
            arr[0] = arr[size - 1];
            arr[size - 1] = temp;
            size--;
            minHeapify(0);

            return arr[size];
        }

    }

    public static void main(String args[]) {
        MinHeap h = new MinHeap(11);
        h.insert(3);
        h.insert(2);
        h.insert(15);
        h.insert(20);
        System.out.print(h.extractMin());
    }

} 
```

## Binary Heap (Decrease Key | Delete)
```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Test {

    public static class MinHeap {
        int arr[];
        int size;
        int capacity;

        MinHeap(int c) {
            size = 0;
            capacity = c;
            arr = new int[c];
        }

        int left(int i) {
            return (2 * i + 1);
        }

        int right(int i) {
            return (2 * i + 2);
        }

        int parent(int i) {
            return (i - 1) / 2;
        }


        public void insert(int x) {
            if (size == capacity) return;
            size++;
            arr[size - 1] = x;

            for (int i = size - 1; i != 0 && arr[parent(i)] > arr[i]; ) {
                int temp = arr[i];
                arr[i] = arr[parent(i)];
                arr[parent(i)] = temp;
                i = parent(i);
            }
        }

        public void minHeapify(int i) {
            int lt = left(i);
            int rt = right(i);
            int smallest = i;
            if (lt < size && arr[lt] < arr[i])
                smallest = lt;
            if (rt < size && arr[rt] < arr[smallest])
                smallest = rt;
            if (smallest != i) {
                int temp = arr[i];
                arr[i] = arr[smallest];
                arr[smallest] = temp;
                minHeapify(smallest);
            }
        }

        public int extractMin() {
            if (size <= 0)
                return Integer.MAX_VALUE;
            if (size == 1) {
                size--;
                return arr[0];
            }
            int temp = arr[0];
            arr[0] = arr[size - 1];
            arr[size - 1] = temp;
            size--;
            minHeapify(0);

            return arr[size];
        }

        void decreaseKey(int i, int x) {
            arr[i] = x;
            while (i != 0 && arr[parent(i)] > arr[i]) {
                int temp = arr[i];
                arr[i] = arr[parent(i)];
                arr[parent(i)] = temp;
                i = parent(i);
            }
        }

        void deleteKey(int i) {
            decreaseKey(i, Integer.MIN_VALUE);
            extractMin();
        }

    }

    public static void main(String args[]) {
        MinHeap h = new MinHeap(11);
        h.insert(3);
        h.insert(2);
        h.deleteKey(0);
        h.insert(15);
        h.insert(20);
        System.out.println(h.extractMin());
        h.decreaseKey(2, 1);
        System.out.println(h.extractMin());
    }

} 
```

## Binary Heap ( Build Heap ) IMPORTANT
```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Test {

    public static class MinHeap {
        int arr[];
        int size;
        int capacity;

        MinHeap(int c) {
            size = 0;
            capacity = c;
            arr = new int[c];
        }

        int left(int i) {
            return (2 * i + 1);
        }

        int right(int i) {
            return (2 * i + 2);
        }

        int parent(int i) {
            return (i - 1) / 2;
        }

        public void minHeapify(int i) {
            int lt = left(i);
            int rt = right(i);
            int smallest = i;
            if (lt < size && arr[lt] < arr[i])
                smallest = lt;
            if (rt < size && arr[rt] < arr[smallest])
                smallest = rt;
            if (smallest != i) {
                int temp = arr[i];
                arr[i] = arr[smallest];
                arr[smallest] = temp;
                minHeapify(smallest);
            }
        }
		// IMPORTANT
        public void buildHeap() {
            for (int i = (size - 2) / 2; i >= 0; i--)
                minHeapify(i);
        }

    }

    public static void main(String args[]) {
        MinHeap h = new MinHeap(11);
    }

} 
```

