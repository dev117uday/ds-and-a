---
description: Mathematical Questions
---

# Maths

## Basic Maths

### Sum of AP

$$
sum = n/2*(2a+(n-1)d
$$

### Sum of GP

$$
sum of GP = a(1-r^n)/1-r
$$

**Mean :** sum of all numbers divided by number of numbers

**Median** :

* For odd number of numbers : middle number 
* For even number of numbers : = \(mean\_of\_2\_middle anumbers\)/2

**LCM**

![\mathrm {lcm} \(a,b\) = \frac {\|a \cdot b\|}{gcd \(a,b\)}](https://www.gstatic.com/education/formulas2/-1/en/greatest_common_divisor.svg)

## Number of Digits

### Number of Digits in a number \(iteratively\)

```go
package main

import "fmt"

func main ( String[] args ) {

    num := 123456
    len := 0
    for num > 0 {
        num = num/10
        len++
    }
    fmt.Println(len)

}
```

### Number of Digits in a number \(recursively\)

```go
package main

import "fmt"

func countDigits(num int) int {
    if num == 0 {
        return 0
    }
    return 1+countDigits(num/10)
}

func main ( String[] args ) {

    num := 123456
    fmt.Println(countDigits(num))

}
```

### Number of Digits in a number \(mathematically\)

```go
package main

import (
    "fmt"
    "math"
)


func main ( String[] args ) {

    var num float64 = 123456
    fmt.Println(math.Floor(math.Log10(num)+1))

}
```

## Greatest C Divisor or Highest C Factor \( GCD\|HCF \)

```go
package main

import (
    "fmt"
)

func gcd(m int, n int) int {

    if m == 0 {
        return n
    }
    return gcd(n%m, m)
}

func main ( String[] args ) {
    fmt.Println(gcd(28, 8))
}
```

## First N Prime

```go
package main

import (
    "fmt"
)

func firstNprime(number int) []int {

    var array []int
    for i := 1; i <= number; i++ {
        if i == 1 {
            continue
        }
        flag := 0
        for j := 2; j <= i/2; j++ {
            if i%j == 0 {
                flag = 1
                break
            }
        }
        if flag == 0 {
            array = append(array, i)
        }
    }
    return array

}

func main ( String[] args ) {
    fmt.Println(firstNprime(100))
}
```

