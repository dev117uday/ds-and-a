# Bit Manipulation

## Check if the kth bit is set or not

```java
// Java program to check if  
// k-th bit of a given number  
// is set or not using right  
// shift operator. 

import java.io.*;
import java.util.*;
import java.lang.*;

class GFG  
{ 
    static void isKthBitSet(int n, int k) 
    { 
        if (((n >> (k - 1)) & 
                   1) == 1) 
            System.out.println("SET"); 
        else
            System.out.println("NOT SET"); 
    } 

    // Driver code 
    public static void main (String[] args)  
    { 
        int n = 5, k = 1; 
        isKthBitSet(n, k); 
    } 
}
```

## Check if a number is a power of 2

```java
// Java program to efficiently  
// check for power for 2 

class Test 
{ 
    /* Method to check if x is power of 2*/
    static boolean isPowerOfTwo (int x) 
    { 
      /* First x in the below expression is  
        for the case when x is 0 */
        return x!=0 && ((x&(x-1)) == 0); 

    } 

    // Driver method 
    public static void main(String[] args)  
    { 
         System.out.println(isPowerOfTwo(31) ? "Yes" : "No"); 
         System.out.println(isPowerOfTwo(64) ? "Yes" : "No"); 

    } 
}
```

## Count set bits

```java
// Java program to Count set  
// bits in an integer  
import java.io.*;
import java.util.*;
import java.lang.*;

class countSetBits 
{ 
    /* Function to get no of set  
    bits in binary representation  
    of passed binary no. */
    static int countSetBits(int n) 
    { 
        int count = 0; 
        while (n > 0) 
        { 
            n &= (n - 1) ; 
            count++; 
        } 
        return count; 
    } 

    // driver program 
    public static void main(String args[]) 
    { 
           int i = 9; 
        System.out.println(countSetBits(i)); 
    } 
}
```

## Find the Number Occurring Odd Number of Times

```java
//Java program to find the element occurring odd number of times 
import java.util.*;
import java.io.*;
import java.lang.*;
class OddOccurance  
{ 
    int getOddOccurrence(int ar[], int ar_size)  
    { 
        int i; 
        int res = 0; 
        for (i = 0; i < ar_size; i++)  
        { 
            res = res ^ ar[i]; 
        } 
        return res; 
    } 

    public static void main(String[] args)  
    { 
        OddOccurance occur = new OddOccurance(); 
        int ar[] = new int[]{2, 3, 5, 4, 5, 2, 4, 3, 5, 2, 4, 4, 2}; 
        int n = ar.length; 
        System.out.println(occur.getOddOccurrence(ar, n)); 
    } 
}
```

## Longest substring with count of 1s more than 0s

```java
// Java program to find largest substring 
// having count of 1s more than count 
// count of 0s. 
import java.util.*;
import java.io.*;
import java.lang.*;

class GFG 
{ 

    // Function to find longest substring 
    // having count of 1s more than count 
    // of 0s. 
    static int findLongestSub(String bin) 
    { 
        int n = bin.length(), i; 

        // To store sum. 
        int sum = 0; 

        // To store first occurrence of each 
        // sum value. 
        HashMap<Integer, 
                Integer> prevSum = new HashMap<>(); 

        // To store maximum length. 
        int maxlen = 0; 

        // To store current substring length. 
        int currlen; 
        for (i = 0; i < n; i++) 
        { 

            // Add 1 if current character is 1 
            // else subtract 1. 
            if (bin.charAt(i) == '1') 
                sum++; 
            else
                sum--; 

            // If sum is positive, then maximum 
            // length substring is bin[0..i] 
            if (sum > 0) 
            { 
                maxlen = i + 1; 
            } 

            // If sum is negative, then maximum 
            // length substring is bin[j+1..i], where 
            // sum of substring bin[0..j] is sum-1. 
            else if (sum <= 0) 

            { 
                if (prevSum.containsKey(sum - 1)) 
                { 
                    currlen = i - (prevSum.get(sum - 1) == null ? 1 : 
                                prevSum.get(sum - 1)); 
                    maxlen = Math.max(maxlen, currlen); 
                } 
            } 

            // Make entry for this sum value in hash 
            // table if this value is not present. 
            if (!prevSum.containsKey(sum)) 
                prevSum.put(sum, i); 
        } 
        return maxlen; 
    } 

    // Driver code 
    public static void main(String[] args) 
    { 
        String bin = "1010"; 
        System.out.println(findLongestSub(bin)); 
    } 
}
```

## Generate power set

```java
// Java program for power set 
import java.io.*;
import java.util.*;
import java.lang.*;

public class GFG { 

    static void printPowerSet(char []set, 
                            int set_size) 
    { 

        /*set_size of power set of a set 
        with set_size n is (2**n -1)*/
        long pow_set_size = 
            (long)Math.pow(2, set_size); 
        int counter, j; 

        /*Run from counter 000..0 to 
        111..1*/
        for(counter = 0; counter < 
                pow_set_size; counter++) 
        { 
            for(j = 0; j < set_size; j++) 
            { 
                /* Check if jth bit in the 
                counter is set If set then 
                print jth element from set */
                if((counter & (1 << j)) > 0) 
                    System.out.print(set[j]); 
            } 

            System.out.println(); 
        } 
    } 

    // Driver program to test printPowerSet 
    public static void main (String[] args) 
    { 
        char []set = {'a', 'b', 'c'}; 
        printPowerSet(set, 3); 
    } 
}
```

