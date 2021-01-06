---
description: All sorting
---

# Sorting

### Insertion Sort

```java
class Program {
    static void sort(int arr[]) {
        int n = arr.length;
        for (int i = 1; i < n; ++i) {
            int key = arr[i];
            int j = i - 1;
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = key;
            arr_printer(arr);
        }
    }
    static void arr_printer(int[] arr) {
        for (int key : arr) {
            System.out.print(key+" ");
        }
        System.out.print("\n");
    }

    static void printArray(int arr[]) {
        int n = arr.length;
        for (int i = 0; i < n; ++i)
            System.out.print(arr[i] + " ");

        System.out.println();
    }

    public static void main(String args[]) {
        int arr[] = { 13,12,11,10,6,5 };
        sort(arr);
        printArray(arr);
    }
}
```



