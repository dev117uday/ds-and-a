---
description: Mathematical Questions
---

# Mathematics

All things maths related



#### Number of Digits in a number \(iteratively\)

```text
package main

import "fmt"

func main() {

    num := 123456
    len := 0
    for num > 0 {
        num = num/10
        len++
    }
    fmt.Println(len)

}
```

#### Number of Digits in a number \(recursively\)

```text
package main

import "fmt"

func countDigits(num int) int {
    if num == 0 {
        return 0
    }
    return 1+countDigits(num/10)
}

func main() {

    num := 123456
    fmt.Println(countDigits(num))

}
```

#### Number of Digits in a number \(mathematically\)

```text
package main

import (
    "fmt"
    "math"
)


func main() {

    var num float64 = 123456
    fmt.Println(math.Floor(math.Log10(num)+1))

}
```

#### Sum of AP

$$
sum = n/2*(2a+(n-1)d
$$

#### Sum of GP

$$
sum of GP = a(1-r^n)/1-r
$$

**Mean :** sum of all numbers divided by number of numbers

**Median** : 

* For odd number of numbers : middle number 
* For even number of numbers : = \(mean\_of\_2\_middle anumbers\)/2

**LCM**  

![\mathrm {lcm} \(a,b\) = \frac {\|a \cdot b\|}{gcd \(a,b\)}](https://www.gstatic.com/education/formulas2/-1/en/greatest_common_divisor.svg)



