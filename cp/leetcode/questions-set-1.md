---
description: Leetcode solutions set 1
---

# Questions \(Set 1\)

### binary-linkedlist.go

```text
import "math"

func getDecimalValue(head *ListNode) int {
    var list []int
    var sum float64 = 0
    for head != nil {
        list = append(list, head.Val)
        head = head.Next
    }
    length := len(list) - 1
    for i := 0; i < len(list); i++ {
        if list[i] == 1 {
            sum += math.Pow(float64(2), float64(length-i))
        }
    }
    return int(sum)
}
```

### consecutive\_char.go

```text
func maxPower(s string) int {
    count := 0
    max := 0
    for i:=1; i<len(s);i++ {
        if s[i-1] == s[i] {
            count++
        } else {
            if max < count {
                max = count
            }
            count=0
        }
    } 
    if max < count {
        max = count
    }
    max++
    return max
}
```

### create-target-array-in-the-given-order.go

```text
func createTargetArray(nums []int, index []int) []int {
    if len(index) == 1 {
        return nums
    }

    var result []int
    for i:=0; i<len(nums); i++ {
        if index[i] >= i {
            result = append(result,nums[i])
        } else {

            var temp []int
            for j:=0; j<index[i]; j++ {
                temp = append(temp,result[j])
            }
            temp = append(temp,nums[i])
            for j:=index[i]; j<len(result); j++ {
                temp = append(temp,result[j])
            }
            result = result[:0]
            for j:=0; j<len(temp); j++ {
                result = append(result,temp[j])
            }

        }
    }
    return result
}
```

### decompress-run-length-encoded-list.go

```text
func decompressRLElist(nums []int) []int {
    var result []int
    for i:=0; i<len(nums)-1; i = i+2 {
        for j:=0; j<nums[i]; j++ {
            result = append(result,nums[i+1])
        }
    }
    return result
}
```

### defanging-an-ip-address.go

```text
func defangIPaddr(address string) string {
    var result string
    for i:=0; i<len(address); i++ {
        if string(address[i]) == "." {
            result = result + "[.]"
        } else {
            result = result + string(address[i])
        }
    }
    return result
}
```

### duplicate\_zeros.go

```text
package main

import "fmt"

func main() {

    var arr = []int{1, 0, 2, 3, 0, 4, 5, 0}
    var lenArr = len(arr) - 1

    for i := 0; i < lenArr; i++ {
        if arr[i] == 0 {
            copy(arr[i+1:], arr[i:])
            arr[i] = 0
            i++
        }

    }

    fmt.Println(arr)

}
```

### duplicateZeros.go

```text
func duplicateZeros(arr []int)  {
    var lenArr = len(arr) - 1

    for i := 0; i < lenArr; i++ {
        if arr[i] == 0 {
            copy(arr[i+1:], arr[i:])
            arr[i] = 0
            i++
        }

    }
}
```

### evenSizeNumbers.go

```text
func findNumbers(nums []int) int {

    answer := 0
    for i:=0;i<len(nums);i++ {
        if numberOfDigits(nums[i])%2 == 0 {
            answer++
        }
    }
    return answer
}

func numberOfDigits (num int) int {
    count := 0
    for num > 0 {
        num = num/10
        count++
    }
    return count
}
```

### findMaxCons.go

```text
func findMaxConsecutiveOnes(nums []int) int {
    counter := 0
    max := 0 
    for i:=0; i<len(nums); i++ {
        if nums[i] == 1 {
            counter++
        } else {
            if counter > max {
                max = counter
            }
            counter = 0
        }
    }
    if counter > max {
       return counter
    } else {
        return max
    }
}
```

### happy-number.go

```text
func isHappy(n int) bool {
    var index int = 0
    set := make(map[int]bool)
    set[n] = true
    for {
        var temp int = 0
        for n != 0 {
            index = n % 10
            temp = temp + index*index
            n = n / 10
        }

        if temp == 1 {
            return true
        }

        _, answer := set[temp]
        if answer == true {
            return false
        } else {
            set[temp] = true
            n = temp
        }
    }
}
```

### how-many-numbers-are-smaller-than-the-current-number.go

```text
func smallerNumbersThanCurrent(nums []int) []int {
    var result []int
    for i:=0; i<len(nums); i++ {
        count := 0
        for j:=0; j<len(nums); j++ {
            if nums[j] < nums[i] && j!=i {
                count++
            }
        }
        result = append(result,count)
    }
    return result
}
```

### jewels-and-stones.go

```text
func numJewelsInStones(J string, S string) int {
    result := 0

    for i:=0; i<len(J); i++ {
        for j:=0; j<len(S); j++ {
            if S[j] == J[i] {
                result++
            }
        }
    }
    return result
}
```

### kids-with-the-greatest-number-of-candies.go

```text
func kidsWithCandies(candies []int, extraCandies int) []bool {
    var result []bool
    biggest := candies[0]
    for _,value := range candies {
        if value > biggest {
            biggest = value
        }
    }

    for _,value := range candies {
        if extraCandies + value >= biggest {
            result = append(result,true)
        } else {
            result = append(result,false)
        }
    }
    return result
}
```

### mergeSortedArray.go

```text
// wrong method
func merge(nums1 []int, m int, nums2 []int, n int) {
	for m > 0 || n > 0 {
		if n == 0 {
			break
		}
		if m == 0 {
			nums1[n-1] = nums2[n-1]
			n--
			continue
		}
		if nums1[m-1] > nums2[n-1] {
			nums1[m+n-1] = nums1[m-1]
			m--
		} else {
			nums1[m+n-1] = nums2[n-1]
			n--
		}
	}
}
```

### number-of-good-pairs.go

```text
func numIdenticalPairs(nums []int) int {
    result := 0
    for i:=0; i<len(nums); i++ {
        for j:=i+1; j<len(nums); j++ {
            if nums[i] == nums[j] {
                result++
            }
        }
    }
    return result
}
```

### number-of-steps-to-reduce-a-number-to-zero.go

```text
func numberOfSteps (num int) int {
    count := 0
    for num > 0 {
        if num%2 == 0 {
            num = num/2
            count++
        } else {
            num--
            count++
        }
    }
    return count
}
```

### removeDuplicate.go

```text
func removeDuplicates(nums []int) int {
    for i := 0; i < len(nums)-1; i++ {
        if nums[i] == nums[i+1] {
            copy(nums[i:], nums[i+1:])
            nums = nums[:len(nums)-1]
            i--
        }
    }
    return len(nums)
}
```

### removeElement.go

```text
func removeElement(nums []int, val int) int {
    answer := 0
    for i := 0; i < len(nums); i++ {
        if nums[i] == val {
            copy(nums[i:], nums[i+1:])
            nums[len(nums)-1] = 0
            nums = nums[:len(nums)-1]
            answer++
            i--
        }
    }

    return nums
}
```

### running-sum-of-1d-array.go

```text
func runningSum(nums []int) []int {
    var result []int
    sum := 0
    for _,value := range nums{
        sum = sum + value
        result = append(result,sum)
    }
    return result
}
```

### shuffle-string.go

```text
func restoreString(s string, indices []int) string {
    var result string = ""
    for i:=0; i<len(indices); i++ {
        for j:=0; j<len(indices); j++ {
            if i == indices[j]{
                result = result + string(s[j])
                temp := indices
                var indices []int
                for x:=0; x<=j-1; x++ {
                    indices = append(indices,temp[x])
                } 
                for x:=j+1; x<len(temp); x++ {
                    indices = append(indices,temp[x])
                } 
                break
            }

        }
    }
    return result
}
```

### shuffle-the-array.go

```text
func shuffle(nums []int, n int) []int {
    var result []int
    length := len(nums)
    for i:=0; i<length/2; i++ {
        result = append(result,nums[i])
        result = append(result,nums[length/2+i])
    }
    return result
}
```

### split-a-string-in-balanced-strings.go

```text
func balancedStringSplit(s string) int {
    count := 0
    lCount := 0
    rCount :=0
    for i:=0; i<len(s); i++ {
        if string(s[i]) == string("L") {
            lCount++
        } else {
            rCount++
        }
        if lCount == rCount {
            count++
            lCount = 0
            rCount = 0
        }
    }
    return count
}
```

### squareOfSortedArray.go

```text
func sortedSquares(A []int) []int {
    var answer []int
    for _,val := range A {
        answer = append(answer, val*val)
    }
     return bubblesort(answer)
}

func bubblesort(items []int) []int {
    var (
        n = len(items)
        sorted = false
    )
    for !sorted {
        swapped := false
        for i := 0; i < n-1; i++ {
            if items[i] > items[i+1] {
                items[i+1], items[i] = items[i], items[i+1]
                swapped = true
            }
        }
        if !swapped {
            sorted = true
        }
        n = n - 1
    }
    return items
}
```

### subtract-the-product-and-sum-of-digits-of-an-integer.go

```text
func subtractProductAndSum(n int) int {
    result := []int{1,0}
    for n>0 {
        temp := n%10
        result[0] = result[0]*temp
        result[1] = result[1]+temp
        n = n/10
    }
    return result[0]-result[1]
}
```

### xor-operation-in-an-array.go

```text
func xorOperation(n int, start int) int {
    temp := start
    for i:=1; i<n; i++ {
        temp = temp ^ (start+2*i)
    }
    return temp
}
```

### 

```text

```



