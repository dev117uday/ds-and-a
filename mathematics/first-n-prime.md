---
description: To find the first N prime numbers
---

# First N Prime

Go : 

```text
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

func main() {
	fmt.Println(firstNprime(100))
}
```



