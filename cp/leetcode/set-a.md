# Set A

### Running Sum of 1-d Array

```go
func runningSum(nums []int) []int {
    var result []int
    sum := 0
    for _,val := range nums {
        sum += val
        result = append(result,sum)
    }
    return result
}
```

### Defanging an IP Address

```go
func defangIPaddr(address string) string {
    var str string
    for _,val := range address {
        if val >= 48 && val <= 57 {
            str += string(val)
        } else {
            str += "[.]"
        }
    }
    return str
}
``#`

## Kids With the Greatest Number of Candies

```go
func kidsWithCandies(candies []int, extraCandies int) []bool {
    max := 0
    for _,val := range candies {
        if val > max {
            max = val
        }
    }
    var result []bool 
    for _,val := range candies {
        if max-val <= extraCandies {
            result = append(result,true)
        } else {
            result = append(result,false)
        }
    }
    return result
}
```

### Richest Customer Wealth

```go
func maximumWealth(accounts [][]int) int {
    max := 0
    sum := 0
    for i:=0;i<len(accounts);i++ {
        sum = 0
        for j:=0;j<len(accounts[i]);j++ {
            sum += accounts[i][j]
        }    
        if max < sum {
            max = sum
        }
    }
    return max
}
```

### Shuffle the Array

```go
func shuffle(nums []int, n int) []int {
    var result []int
    l := len(nums)/2
    for i:=0;i<len(nums)/2;i++ {
        result = append(result , nums[i])
        result = append(result , nums[i+l])
    }
    return result
}
```

### Number of Good Pairs

```go
func numIdenticalPairs(nums []int) int {
    count := 0
    for i:=0;i<len(nums)-1;i++ {
        for j:=i+1;j<len(nums);j++ {
            if nums[i]==nums[j] && i < j {
                count++
            }
        }
    }    
    return count
}
```

### Jewels and Stones

```go
func numJewelsInStones(jewels string, stones string) int {
  jewelCount := 0
  jewelMap := map[string]bool {}
  
  for _, jewel := range jewels {
    jewelMap[string(jewel)] = true
  }
  
  for _, stone := range stones {
    _, ok := jewelMap[string(stone)]
    
    if ok {
      jewelCount++
    }
  }
  
  return jewelCount
}
```

### Remove Duplicates from Sorted List II

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode t = new ListNode(0);
        t.next = head;

        ListNode p = t;
        while(p.next!=null&&p.next.next!=null) {
            if(p.next.val == p.next.next.val) {
                int dup = p.next.val;
                while(p.next!=null&&p.next.val==dup) {
                    p.next = p.next.next;
                }
            } else {
                p=p.next;
            }
        }
        return t.next;
    }
}
```

### Find a Corresponding Node of a Binary Tree in a Clone of That Tree

```java
class Solution {
    public final TreeNode getTargetCopy(final TreeNode original, final TreeNode cloned, final TreeNode target) {
        if(original == null){
            return null;
        }
        
        if(original == target){
            return cloned;
        }
        
        TreeNode left = getTargetCopy(original.left, cloned.left, target);
        if(left != null){
            return left;
        }
        
        TreeNode right = getTargetCopy(original.right, cloned.right, target);
        if(right != null){
            return right;
        }
        
        return null;
    }
}
```

### Merge Two Sorted Lists

```java
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    ListNode head = new ListNode(0);
    ListNode p=head;
 
    ListNode p1=l1;
    ListNode p2=l2;
    while(p1!=null && p2!=null){
        if(p1.val < p2.val){
            p.next = p1;
            p1 = p1.next;
        }else{
            p.next = p2;
            p2 = p2.next;
        }
        p=p.next;
    }
 
    if(p1!=null){
        p.next = p1;
    }
 
    if(p2!=null){
        p.next = p2;
    }
 
    return head.next;
}
```

### Distribute Candies
```go
func distributeCandies(candyType []int) int {
    num := len(candyType)/2
    count := 0
    hashMap := make(map[int]int)
    for i,val := range candyType {
        hashMap[val] = i
        count++
    }
    return min(num,len(hashMap))
}

func min(a,b int) int {
    if a > b {
        return b
    }
    return a
}
```

### Set Mismatch

```go
func findErrorNums(nums []int) []int {
	var a int
	var b int
	for i := 0; i < len(nums); i++ {
		index := abs(nums[i]) - 1
		if nums[index] < 0 {
			b = abs(nums[i])
		} else {
			nums[index] = -1 * nums[index]
		}
	}
	for i := 0; i < len(nums); i++ {
		if nums[i] > 0 {
			a = i + 1
			break
		}
	}
	return []int{b, a}
}

func abs(a int) int {
	if a < 0 {
		return -1 * a
	}
	return a
}
```

### Missing Number

```java
func missingNumber(nums []int) int {
    sum := 0
    for i:=0;i<len(nums);i++ {
        sum += nums[i]
    }
    length := len(nums)
    totalSum := (length*(length+1))/2
    ans := totalSum - sum 
    return ans
}
```











