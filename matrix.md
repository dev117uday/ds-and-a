---
description: Another world
---

# Matrix

## Check if the element is present in row and column wise sorted matrix

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Program
{
    public static void main ( String[] args ) {
        int mat[][] = new int[][]{};
        int ele = 90;

        System.out.println(isPresent(mat, ele, 3, 4) ? "yes" : "no");
    }

    static boolean isPresent(int mat[][], int ele, int m, int n)
    {
        int row = 0, col = 3;
        while(row < m && col >= 0)
        {
            if(mat[row][col] < ele)
              row++;
            else if(mat[row][col] > ele)
               col--;
            else if(mat[row][col] == ele)
              return true;
        }
        return false;
    }
}
```

## Boundary traversal of matrix

```java
// JAVA Code for Boundary elements of a Matrix 
class Program { 

    public static void printBoundary(int a[][], int m, 
                                    int n) 
    { 
        for (int i = 0; i < m; i++) { 
            for (int j = 0; j < n; j++) { 
                if (i == 0) 
                    System.out.print(a[i][j] + " "); 
                else if (i == m - 1) 
                    System.out.print(a[i][j] + " "); 
                else if (j == 0) 
                    System.out.print(a[i][j] + " "); 
                else if (j == n - 1) 
                    System.out.print(a[i][j] + " "); 
                else
                    System.out.print("  "); 
            } 
            System.out.println(""); 
        } 
    } 

    /* Driver program to test above function */
    public static void main ( String[] args ) 
    { 
        int a[][] = { { 1, 2, 3, 4 }, { 5, 6, 7, 8 }, { 1, 2, 3, 4 }, { 5, 6, 7, 8 } }; 

        printBoundary(a, 4, 4); 
    } 
}
```

## Spirally traversing of matrix

```java
// Java program to print a given matrix in spiral form 
import java.io.*; 

class Program { 
    // Function print matrix in spiral form 
    static void spiralPrint(int m, int n, int a[][]) 
    { 
        int i, k = 0, l = 0; 
        /* k - starting row index 
        m - ending row index 
        l - starting column index 
        n - ending column index 
        i - iterator 
        */

        while (k < m && l < n) { 
            // Print the first row from the remaining rows 
            for (i = l; i < n; ++i) { 
                System.out.print(a[k][i] + " "); 
            } 
            k++; 

            // Print the last column from the remaining columns 
            for (i = k; i < m; ++i) { 
                System.out.print(a[i][n - 1] + " "); 
            } 
            n--; 

            // Print the last row from the remaining rows */ 
            if (k < m) { 
                for (i = n - 1; i >= l; --i) { 
                    System.out.print(a[m - 1][i] + " "); 
                } 
                m--; 
            } 

            // Print the first column from the remaining columns */ 
            if (l < n) { 
                for (i = m - 1; i >= k; --i) { 
                    System.out.print(a[i][l] + " "); 
                } 
                l++; 
            } 
        } 
    } 

    // driver program 
    public static void main ( String[] args ) 
    { 
        int R = 3; 
        int C = 6; 
        int a[][] = { { 1, 2, 3, 4, 5, 6 }, 
                    { 7, 8, 9, 10, 11, 12 }, 
                    { 13, 14, 15, 16, 17, 18 } }; 
        spiralPrint(R, C, a); 
    } 
}
```

