---
description: To find the greatest common divisor
---

# Greatest Common Divisor \( GCD \)

Go : 

```text
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

func main() {
	fmt.Println(gcd(28, 8))
}
```



