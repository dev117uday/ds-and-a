# Array

## Reverse an array

```java
import java.io.*;
class Program {
    
    static void reverse(int arr[], int n)
    {
        for(int i = 0; i < n/2; i++)
        {
            int temp = arr[i];
            arr[i] = arr[n-i-1];
            arr[n-i-1] = temp;
        }
    }
	public static void main () {
		int arr[] = new int[]{2, 8, 7, 10, 5};
		int n = arr.length;
		
		reverse(arr, n);
		for(int i = 0; i < n; i++)
		  System.out.print(arr[i] + " ");
	}
}
```

## Rotate an array

```java
import java.io.*;
import java.util.*;
import java.lang.*;

class Program {
    
    static void reverse(int arr[], int start, int end)
    {
        int temp = 0;
        while(start < end)
        {
            temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }
    static void rotateByd(int arr[], int d, int n)
    {
        reverse(arr, 0, d-1);
        reverse(arr, d, n-1);
        reverse(arr, 0, n-1);
    }
	public static void main () 
	{
	    int arr[] = new int[]{2, 8, 7, 10, 5};
	    int n = arr.length;
	    int d = 3;
	    
	    rotateByd(arr, d, n);
	    for(int i = 0; i < n; i++)
	     System.out.print(arr[i] + " ");
	}
}
```

## Leaders in an array

```java
class LeadersInArray 
{ 
	/* Java Function to print leaders in an array */
	void printLeaders(int arr[], int size) 
	{ 
		int max_from_right = arr[size-1]; 

		/* Rightmost element is always leader */
		System.out.print(max_from_right + " "); 
	
		for (int i = size-2; i >= 0; i--) 
		{ 
			if (max_from_right < arr[i]) 
			{		 
			max_from_right = arr[i]; 
			System.out.print(max_from_right + " "); 
			} 
		}	 
	} 

	/* Driver program to test above functions */
	public static void main() 
	{ 
		LeadersInArray lead = new LeadersInArray(); 
		int arr[] = new int[]{16, 17, 4, 3, 5, 2}; 
		int n = arr.length; 
		lead.printLeaders(arr, n); 
	} 
} 

```

## Trapping Rainwater

```java
// Java program to find maximum amount of water that can 
// be trapped within given set of bars. 

class Test {
    static int arr[] = new int[]{0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1};

    // Method for maximum amount of water 
    static int findWater(int n) {
        // left[i] contains height of tallest bar to the 
        // left of i'th bar including itself 
        int left[] = new int[n];

        // Right [i] contains height of tallest bar to 
        // the right of ith bar including itself 
        int right[] = new int[n];

        // Initialize result 
        int water = 0;

        // Fill left array 
        left[0] = arr[0];
        for (int i = 1; i < n; i++)
            left[i] = Math.max(left[i - 1], arr[i]);

        // Fill right array 
        right[n - 1] = arr[n - 1];
        for (int i = n - 2; i >= 0; i--)
            right[i] = Math.max(right[i + 1], arr[i]);

        // Calculate the accumulated water element by element 
        // consider the amount of water on i'th bar, the 
        // amount of water accumulated on this particular 
        // bar will be equal to min(left[i], right[i]) - arr[i] . 
        for (int i = 0; i < n; i++)
            water += Math.min(left[i], right[i]) - arr[i];

        return water;
    }

    // Driver method to test the above function 
    public static void main() {

        System.out.println("Maximum water that can be accumulated is " +
                findWater(arr.length));
    }
} 

```

## Stock buy and sell

```java
import java.util.ArrayList;

// Solution structure
class Interval {
    int buy, sell;
}

class StockBuySell {
    // This function finds the buy sell schedule for maximum profit
    void stockBuySell(int[] price, int n) {
        // Prices must be given for at least two days
        if (n == 1)
            return;

        int count = 0;

        // solution array
        ArrayList<Interval> sol = new ArrayList<Interval>();

        // Traverse through given price array
        int i = 0;
        while (i < n - 1) {
            // Find Local Minima. Note that the limit is (n-2) as we are
            // comparing present element to the next element.
            while ((i < n - 1) && (price[i + 1] <= price[i]))
                i++;

            // If we reached the end, break as no further solution possible
            if (i == n - 1)
                break;

            Interval e = new Interval();
            e.buy = i++;
            // Store the index of minima

            // Find Local Maxima. Note that the limit is (n-1) as we are
            // comparing to previous element
            while ((i < n) && (price[i] >= price[i - 1]))
                i++;

            // Store the index of maxima
            e.sell = i - 1;
            sol.add(e);

            // Increment number of buy/sell
            count++;
        }

        // print solution
        if (count == 0)
            System.out.println("There is no day when buying the stock "
                    + "will make profit");
        else
            for (int j = 0; j < count; j++)
                System.out.println("Buy on day: " + sol.get(j).buy
                        + "	 "
                        + "Sell on day : " + sol.get(j).sell);

        return;
    }

    public static void main() {
        StockBuySell stock = new StockBuySell();

        // stock prices on consecutive days
        int[] price = {100, 180, 260, 310, 40, 535, 695};
        int n = price.length;

        // fucntion call
        stock.stockBuySell(price, n);
    }
}
```

## Find maximum \(or minimum\) sum of a subarray of size k

```java
// JAVA Code for Find maximum (or minimum) 
// sum of a subarray of size k 

import java.util.*;

class Program {

    // Returns maximum sum in a subarray of size k. 
    public static int maxSum(int[] arr, int n, int k) {
        // k must be greater 
        if (n < k) {
            System.out.println("Invalid");
            return -1;
        }

        // Compute sum of first window of size k 
        int res = 0;
        for (int i = 0; i < k; i++)
            res += arr[i];

        // Compute sums of remaining windows by 
        // removing first element of previous 
        // window and adding last element of 
        // current window. 
        int curr_sum = res;
        for (int i = k; i < n; i++) {
            curr_sum += arr[i] - arr[i - k];
            res = Math.max(res, curr_sum);
        }

        return res;
    }

    /* Driver program to test above function */
    public static void main() {
        int[] arr = {1, 4, 2, 10, 2, 3, 1, 0, 20};
        int k = 4;
        int n = arr.length;
        System.out.println(maxSum(arr, n, k));
    }
} 
```

## Find subarray with given sum

```java
public class Program {
    /* Returns true if the there is a subarray of arr[] with sum equal to
    'sum' otherwise returns false. Also, prints the result */
    static int subArraySum(int[] arr, int n, int sum) {
        int curr_sum = arr[0], start = 0, i;

        // Pick a starting point
        for (i = 1; i <= n; i++) {
            // If curr_sum exceeds the sum, then remove the starting elements
            while (curr_sum > sum && start < i - 1) {
                curr_sum = curr_sum - arr[start];
                start++;
            }

            // If curr_sum becomes equal to sum, then return true
            if (curr_sum == sum) {
                int p = i - 1;
                System.out.println("Sum found between indexes " + start
                        + " and " + p);
                return 1;
            }

            // Add this element to curr_sum
            if (i < n)
                curr_sum = curr_sum + arr[i];

        }

        System.out.println("No subarray found");
        return 0;
    }

    public static void main() {
        int[] arr = {15, 2, 4, 8, 9, 5, 10, 23};
        int n = arr.length;
        int sum = 23;
        subArraySum(arr, n, sum);
    }
}
```

## **N-bonacci numbers**

```java
class Program {

    // Function to print bonacci series 
    static void bonacciseries(int n, int m) {

        // Assuming m > n. 
        int a[] = new int[m];
        for (int i = 0; i < m; i++)
            a[i] = 0;

        a[n - 1] = 1;
        a[n] = 1;

        // Uses sliding window 
        for (int i = n + 1; i < m; i++)
            a[i] = 2 * a[i - 1] - a[i - n - 1];

        // Printing result 
        for (int i = 0; i < m; i++)
            System.out.print(a[i] + " ");
    }

    // Driver's Code 
    public static void main() {
        int N = 5, M = 15;
        bonacciseries(N, M);
    }
} 
```

## Prefix Sum array

```java
// Java Program for Implementing
// prefix sum arrayclass
class Program {
    // Fills prefix sum array
    static void fillPrefixSum(int[] arr, int n,
                              int[] prefixSum) {
        prefixSum[0] = arr[0];

        // Adding present element
        // with previous element
        for (int i = 1; i < n; ++i)
            prefixSum[i] = prefixSum[i - 1] + arr[i];
    }

    // Driver code
    public static void main() {
        int[] arr = {10, 4, 16, 20};
        int n = arr.length;
        int[] prefixSum = new int[n];

        fillPrefixSum(arr, n, prefixSum);

        for (int i = 0; i < n; i++)
            System.out.print(prefixSum[i] + " ");
        System.out.println("");
    }

}
```

## Equilibrium point

```java
// Java program to find equilibrium 
// index of an array 

class EquilibriumIndex {
    int equilibrium(int arr[], int n) {
        int sum = 0; // initialize sum of whole array 
        int leftsum = 0; // initialize leftsum 

        /* Find sum of the whole array */
        for (int i = 0; i < n; ++i)
            sum += arr[i];

        for (int i = 0; i < n; ++i) {
            sum -= arr[i]; // sum is now right sum for index i 

            if (leftsum == sum)
                return i;

            leftsum += arr[i];
        }

        /* If no equilibrium index found, then return 0 */
        return -1;
    }

    // Driver code 
    public static void main() {
        EquilibriumIndex equi = new EquilibriumIndex();
        int arr[] = {-7, 1, 5, 2, -4, 3, 0};
        int arr_size = arr.length;
        System.out.println("First equilibrium index is " +
                equi.equilibrium(arr, arr_size));
    }
} 

```

## Maximum occurred integer in N ranges

```java
import java.io.*;

class Program {

    static int MAX = 1000000;

    // Return the maximum occurred element in all ranges.
    static int maximumOccuredElement(int[] L, int[] R, int n) {
        // Initalising all element of array to 0.
        int[] arr = new int[MAX];

        // Adding +1 at Li index and
        // substracting 1 at Ri index.
        int maxi = -1;
        for (int i = 0; i < n; i++) {
            arr[L[i]] += 1;
            arr[R[i] + 1] -= 1;
            if (R[i] > maxi) {
                maxi = R[i];
            }
        }

        // Finding prefix sum and index
        // having maximum prefix sum.
        int msum = arr[0];
        int ind = 0;
        for (int i = 1; i < maxi + 1; i++) {
            arr[i] += arr[i - 1];
            if (msum < arr[i]) {
                msum = arr[i];
                ind = i;
            }
        }

        return ind;
    }

    // Driver program
    static public void main() {
        int[] L = {1, 4, 9, 13, 21};
        int[] R = {15, 8, 12, 20, 30};
        int n = L.length;
        System.out.println(maximumOccuredElement(L, R, n));
    }
}  
```