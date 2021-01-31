# Set A

## Running Sum of 1-d Array

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

## Defanging an IP Address

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
```

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

## Richest Customer Wealth

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

## Shuffle the Array

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

## Number of Good Pairs

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

## Jewels and Stones

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









