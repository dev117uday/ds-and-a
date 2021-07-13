---
description: lets goooo
---

# BackTracking

## Given a string "ABC", print all combination without "AB"

```sql
import java.util.*;
import java.io.*;
import java.lang.*;

class Gfg
{
    
    public static void permute(String str, int l, int r){
    
        if(l==r){
            System.out.print(str+" ");
            return;
        }else{
            for(int i=l;i<=r;i++){
                if(isSafe(str,l,i,r)){
                str=new String(swap(str, i, l));
                
                permute(str,l+1,r);
                
                str=new String(swap(str, i, l));}
            }   
        }
    }
    
    public static boolean isSafe(String str,int l, int i, int r){
        if(l!=0 && str.charAt(l-1)=='A' && str.charAt(i)=='B')
            return false;
        if(r==(l+1) && str.charAt(i)=='A' && str.charAt(l)=='B')
            return false;
        return true;
    }
    
    public static char[] swap(String str, int i, int j) 
    { 
        char ch[] = str.toCharArray(); 
        char temp = ch[i]; 
        ch[i] = ch[j]; 
        ch[j] = temp; 
        return ch; 
    }
    
    public static void main(String args[])
    {
        String str="ABC";
	
        permute(str,0,str.length()-1); 
    }
}
```

## Rat in a Maze

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Gfg
{
    
    static int N; 
  
    static void printSolution(int sol[][]) 
    { 
        for (int i = 0; i < N; i++) { 
            for (int j = 0; j < N; j++) 
                System.out.print( " " + sol[i][j] + " "); 
            System.out.println(); 
        } 
    } 
  
    static boolean isSafe( int maze[][], int i, int j) 
    { 
        return (i < N && j < N && maze[i][j] == 1); 
    } 
  
    static boolean solveMaze(int maze[][]) 
    { 
        int sol[][] = new int[N][N]; 
  
        if (solveMazeRec(maze, 0, 0, sol) == false) { 
            System.out.print("Solution doesn't exist"); 
            return false; 
        } 
  
        printSolution(sol); 
        return true; 
    } 
  
    static boolean solveMazeRec(int maze[][], int i, int j, int sol[][]) 
    {  
        if (i == N - 1 && j == N - 1 && maze[i][j] == 1) { 
            sol[i][j] = 1; 
            return true; 
        } 
  
        if (isSafe(maze, i, j) == true) {  
            sol[i][j] = 1; 
  
            if (solveMazeRec(maze, i + 1, j, sol)) 
                return true; 
  
            if (solveMazeRec(maze, i, j + 1, sol)) 
                return true; 
   
            sol[i][j] = 0; 
        } 
  
        return false; 
    } 
    
    public static void main(String args[])
    {
        int maze[][] = { { 1, 0, 0, 0 }, 
                         { 1, 1, 0, 1 }, 
                         { 0, 1, 0, 0 }, 
                         { 1, 1, 1, 1 } }; 
  
        N = maze.length; 
        solveMaze(maze); 
    }
}
```

## N Queen Problem

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Gfg
{
    
    static final int N = 4;
    static int board[][] = { { 0, 0, 0, 0 }, 
                    { 0, 0, 0, 0 }, 
                    { 0, 0, 0, 0 }, 
                    { 0, 0, 0, 0 } };
    static void printSolution(int board[][]) 
    { 
        for (int i = 0; i < N; i++) { 
            for (int j = 0; j < N; j++) 
                System.out.print(" " + board[i][j] 
                                 + " "); 
            System.out.println(); 
        } 
    }
  
    static boolean isSafe(int row, int col) 
    { 
        int i, j; 
  
        for (i = 0; i < col; i++) 
            if (board[row][i] == 1) 
                return false; 
  
        for (i = row, j = col; i >= 0 && j >= 0; i--, j--) 
            if (board[i][j] == 1) 
                return false; 
  
        for (i = row, j = col; j >= 0 && i < N; i++, j--) 
            if (board[i][j] == 1) 
                return false; 
  
        return true; 
    } 
  
    static boolean solveRec(int col) 
    { 
        if (col == N) 
            return true; 
  
        for (int i = 0; i < N; i++) {  
            if (isSafe(i, col)) { 
                board[i][col] = 1; 
  
                if (solveRec(col + 1) == true) 
                    return true; 
  
                board[i][col] = 0; 
            } 
        }
        return false;
    }
    
    static  boolean solve() 
    { 
  
        if (solveRec(0) == false) { 
            System.out.print("Solution does not exist"); 
            return false; 
        } 
  
        printSolution(board); 
        return true; 
    }
    
    public static void main(String args[])
    {
        solve(); 
    }
}
```

## **Sudoku Problem**

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class GFG  
{ 
    public static boolean isSafe(int[][] board,int row, int col, int num) 
    { 
     
        for (int d = 0; d < board.length; d++)  
        { 
            
            if (board[row][d] == num) { 
                return false; 
            } 
        } 
  
        for (int r = 0; r < board.length; r++)  
        { 
               
            if (board[r][col] == num)  
            { 
                return false; 
            } 
        }  
        int sqrt = (int)Math.sqrt(board.length); 
        int boxRowStart = row - row % sqrt; 
        int boxColStart = col - col % sqrt; 
  
        for (int r = boxRowStart; 
             r < boxRowStart + sqrt; r++)  
        { 
            for (int d = boxColStart; 
                 d < boxColStart + sqrt; d++)  
            { 
                if (board[r][d] == num)  
                { 
                    return false; 
                } 
            } 
        } 
  
        return true; 
    } 
  
    public static boolean solveSudoku( 
        int[][] board, int n) 
    { 
        int row = -1; 
        int col = -1; 
        boolean isEmpty = true; 
        for (int i = 0; i < n; i++)  
        { 
            for (int j = 0; j < n; j++)  
            { 
                if (board[i][j] == 0)  
                { 
                    row = i; 
                    col = j; 
                    isEmpty = false; 
                    break; 
                } 
            } 
            if (!isEmpty) { 
                break; 
            } 
        } 
  
        if (isEmpty)  
        { 
            return true; 
        } 
        
        for (int num = 1; num <= n; num++)  
        { 
            if (isSafe(board, row, col, num))  
            { 
                board[row][col] = num; 
                if (solveSudoku(board, n))  
                { 
                    // print(board, n); 
                    return true; 
                } 
                else 
                { 
                    // replace it 
                    board[row][col] = 0; 
                } 
            } 
        } 
        return false; 
    } 
  
    public static void print(int[][] board, int N) 
    { 
        for (int r = 0; r < N; r++)  
        { 
            for (int d = 0; d < N; d++) 
            { 
                System.out.print(board[r][d]); 
                System.out.print(" "); 
            } 
            System.out.print("\n"); 
  
            if ((r + 1) % (int)Math.sqrt(N) == 0) 
            { 
                System.out.print(""); 
            } 
        } 
    } 
  
    public static void main(String args[]) 
    { 
  
        int[][] board = new int[][] { 
            { 3, 0, 6, 5, 0, 8, 4, 0, 0 }, 
            { 5, 2, 0, 0, 0, 0, 0, 0, 0 }, 
            { 0, 8, 7, 0, 0, 0, 0, 3, 1 }, 
            { 0, 0, 3, 0, 1, 0, 0, 8, 0 }, 
            { 9, 0, 0, 8, 6, 3, 0, 0, 5 }, 
            { 0, 5, 0, 0, 9, 0, 6, 0, 0 }, 
            { 1, 3, 0, 0, 0, 0, 2, 5, 0 }, 
            { 0, 0, 0, 0, 0, 0, 0, 7, 4 }, 
            { 0, 0, 5, 2, 0, 6, 3, 0, 0 } 
        }; 
        int N = board.length; 
  
        if (solveSudoku(board, N))  
        {  
            print(board, N); 
        } 
        else { 
            System.out.println("No solution"); 
        } 
    } 
}
```



