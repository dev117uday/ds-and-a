---
description: Codeforce A
---

# Questions \(Set 1\)

### 110A.go

```text
package main

import (
    "fmt"
    "os"
)

func main() {

    var number string
    count := 0
    _, _ = fmt.Scanln(&number)

    if number == "7" || number == "4" {
        fmt.Print("NO")
        os.Exit(0)
    }

    for i:=0; i<len(number); i++ {
        if string(number[i]) == "4" || string(number[i]) == "7" {
            continue
        } else {
            count++
            break
        }
    }

    if count == 0 {
        if len(number) == 4 || len(number) == 7 {
            fmt.Println("YES")
        } else {
            fmt.Println("NO")
        }
    } else {

        counter := 0
        for i:=0; i<len(number); i++ {
            if string(number[i]) == "4" || string(number[i]) == "7" {
                counter++
            }
        }

        if counter == 4 || counter == 7 {
            fmt.Println("YES")
        } else {
            fmt.Println("NO")
        }

    }

}
```

### 112A.go

```text
package main

import (
    "fmt"
    "strings"
)

func main() {

    var string1 string
    var string2 string

    _, _ = fmt.Scanln(&string1)
    _, _ = fmt.Scanln(&string2)

    str1 := strings.ToLower(string1)
    str2 := strings.ToLower(string2)

    for i := 0; i < len(str1); i++ {
        if str1[i] > str2[i] {
            fmt.Println("1")
            break
        } else if str1[i] < str2[i] {
            fmt.Println("-1")
            break
        } else if i == len(str1)-1 {
            fmt.Println("0")
            break
        }
    }

}
```

### 116A.go

```text
package main

import "fmt"

func main() {

    var number int = 0
    _, _ = fmt.Scanln(&number)
     var matrix = make([][2]int,number)

     var max,min = 0,0

     for i:=0; i<number; i++ {
         _, _ = fmt.Scan(&matrix[i][0])
         _, _ = fmt.Scan(&matrix[i][1])
         min =  matrix[i][1] - matrix[i][0] + min
        if min > max {
            max = min
        }
     }
     fmt.Println(max)
}
```

### 118A.go

```text
package main

import (
    "fmt"
    "strings"
)

func main() {
    var istring string
    _, _ = fmt.Scan(&istring)
    istring = strings.ToLower(istring)
    temp := strings.Split(istring,"")
    var tempArray = []string{"."}
    for i:=0; i<len(temp); i++ {
        if temp[i] == "a" || temp[i] == "e" || temp[i] == "i" || temp[i] == "u" || temp[i] == "o" || temp[i] == "y" {
            continue
        } else {
            tempArray = append(tempArray,temp[i])
            tempArray = append(tempArray,".")
        }
    }
    tempArray = tempArray[:len(tempArray)-1]
    istring  = strings.Join(tempArray,"")
    fmt.Println(istring)

}
```

### 122A.go

```text
package main

import "fmt"

func main() {
    var num int
    _, _ = fmt.Scan(&num)
    flag := 0
    var check = []int{4,7,47,74,44,444,447,474,477,777,774,744}
    for i:=0; i<len(check); i++ {
        if num%check[i] == 0 {
            flag = 1
        }
    }
    if flag == 1 {
        fmt.Println("YES")
    } else {
        fmt.Println("NO")
    }
}
```

### 133A.go

```text
package main

import (
    "fmt"
    "strings"
)

func main() {
    var istring string
    _, _ = fmt.Scanln(&istring)
    temp :=  strings.Split(istring,"")
    flag := 0
    for i:=0; i<len(temp); i++{
        if temp[i] == "H" || temp[i] == "Q" || temp[i] == "9" {
            fmt.Println("YES")
            flag = 1
            break
        }
    }
    if flag == 0 {
        fmt.Println("NO")
    }
}
```

### 136A.go

```text
package main

import (
    "bufio"
    "fmt"
    "os"
)

var reader *bufio.Reader = bufio.NewReader(os.Stdin)
var writer *bufio.Writer = bufio.NewWriter(os.Stdout)

func printf(f string, a ...interface{}) { fmt.Fprintf(writer, f, a...) }
func scanf(f string, a ...interface{})  { fmt.Fscanf(reader, f, a...) }

func main() {
    var number, i uint8
    _, _ = fmt.Scanln(&number)
    number++
    var oned = make([]uint8, number, number+3)
    for i = 1; i < number; i++ {
        var p uint8
        scanf("%d", &p)
        oned[p] = i
    }

    fmt.Print(oned[1])
    for i := 2; i < len(oned); i++ {
        fmt.Print(" ", oned[i])
    }
    fmt.Print("\n")

}
```

### 158A.go

```text
package main

import (
    "fmt"
    "os"
)

func main() {

    var numberOfParticipants, rating int = 0, 0
    _, _ = fmt.Scan(&numberOfParticipants)
    _, _ = fmt.Scan(&rating)

    var slice = make([]int, numberOfParticipants)
    for i := 0; i < numberOfParticipants; i++ {
        _, _ = fmt.Scan(&slice[i])
    }

    if slice[0] == 0 {
        fmt.Println(0)
        os.Exit(0)
    }

    score := slice[rating-1]
    count := 0

    for i := 0; i < len(slice); i++ {
        if slice[i] >= score && slice[i] != 0 {
            count++
        } else {
            break
        }
    }

    fmt.Println(count)

}
```

### 160A.go

```text
package main

import (
    "fmt"
    "sort"
)

func main() {
    var num int
    _, _ = fmt.Scan(&num)
    var oned = make([]int,num)
    sum := 0
    for i:=0; i<num; i++ {
        fmt.Scan(&oned[i])
        sum = sum + oned[i]
    }
    sort.Sort(sort.Reverse(sort.IntSlice(oned)))
    temp :=0
    count := 0
    for i:=0; i<len(oned); i++ {
        if temp > sum {
            break
        }
        temp = temp+oned[i]
        count++
        sum = sum - oned[i]
    }
    fmt.Println(count)

}
```

### 1A.go

```text
// doesnt work for bi value, refer to cpp version

package main

import (
    "fmt"
    "math"
)

func main() {
    var width float64
    var height float64
    var flagstone float64
    _, _ = fmt.Scan(&width)
    _, _ = fmt.Scan(&height)
    _, _ = fmt.Scan(&flagstone)
    one := math.Ceil(width/flagstone)
    two := math.Ceil(height/flagstone)
    fmt.Println(one*two)
}
```

### 231A.go

```text
package main

import "fmt"

func main(){

    var numberOfRows int = 0
    _,_ = fmt.Scanln(&numberOfRows)

    var twoDMatrix = make([][3]int,numberOfRows)

    for i:=0; i<numberOfRows; i++ {
        for j:=0; j<3; j++ {
            _,_ = fmt.Scan(&twoDMatrix[i][j])
        }
    }

    var count int = 0
    for i:=0; i<numberOfRows; i++ {
        temp := 0
        for j:=0; j<3; j++ {
            if twoDMatrix[i][j] == 1 {
                temp++
            }
        }
        if temp > 1 {
            count++
        }
    }

    fmt.Println(count)

}
```

### 236A.go

```text
package main

import "fmt"

func main() {

    var inputString string
    _, _ = fmt.Scanln(&inputString)

    var hashMap  = make(map[string]string)

    temp := string(inputString[0])

    hashMap[temp] = string(inputString[0])

    for i:=1; i<len(inputString); i++ {
        _,found := hashMap[string(inputString[i])]
        if found {
            continue
        } else {
            hashMap[string(inputString[i])] = string(inputString[i])
        }
    }
    if len(hashMap)%2 == 0 {
        fmt.Println("CHAT WITH HER!")
    } else {
        fmt.Println("IGNORE HIM!")
    }


}
```

### 263A.go

```text
package main

import (
    "fmt"
    "math"
)

func main() {
    var matrix [5][5]int32
    var m, n = 0, 0

    for i := 0; i < 5; i++ {
        for j := 0; j < 5; j++ {
            _, _ = fmt.Scan(&matrix[i][j])
            if matrix[i][j] == 1 {
                m = i
                n = j
            }
        }
    }

    temp := math.Abs(float64(m)-2) + math.Abs(float64(n)-2)
    fmt.Println(temp)
}
```

### 266A.go

```text
package main

import (
    "bufio"
    "fmt"
    "os"
)

func main() {
    var number int32
    _, _ = fmt.Scanln(&number)
    istring, _ := bufio.NewReader(os.Stdin).ReadString('\n')
    xchar := istring[0]
    count := 0

    for i := 1; i < len(istring); i++ {
        if istring[i] == xchar {
            count++
        }
        xchar = istring[i]
    }

    fmt.Println(count)

}
```

### 271A.go

```text
package main

import (
    "fmt"
)

func main() {
    var year uint16
    _, _ = fmt.Scanln(&year)
    for {
        year++
        one := uint16(year / 1000)
        two := uint16((year%1000 - year%100) / 100)
        three := uint16((year/10 - one*100) % 10)
        four := uint16(year % 10)

        if one == two || one == three || one == four || two == three || two == four || three == four {
            continue
        } else {
            fmt.Print(year)
            break
        }
    }
}
```

### 281A.go

```text
package main

import (
    "bufio"
    "fmt"
    "os"
    "strings"
)

func main() {
    istring, _ := bufio.NewReader(os.Stdin).ReadString('\n')
    temp := strings.Split(istring, "")
    temp[0] = strings.ToUpper(temp[0])
    xstr := strings.Join(temp, "")
    fmt.Println(xstr)
}
```

### 282A.go

```text
package main

import (
    "fmt"
)

func main() {
    var bitland []string
    number := 0
    _, _ = fmt.Scanln(&number)
    for number > 0 {
        var istring string
        _, _ = fmt.Scanln(&istring)
        bitland = append(bitland, istring)
        number--
    }
    var count int32 = 0

    for i := 0; i < len(bitland); i++ {
        if string(bitland[i]) == "++X" {
            count++
        } else if string(bitland[i]) == "X++" {
            count++
        } else {
            count--
        }
    }

    fmt.Println(count)
}
```

### 339A.go

```text
package main

import (
    "fmt"
    "sort"
    "strconv"
    "strings"
)

func main() {
    var istring string
    _, _ = fmt.Scanln(&istring)
    xstring := strings.Split(istring, "+")
    var numArray []int
    for i := 0; i < len(xstring); i++ {
        inumber, _ := strconv.Atoi(xstring[i])
        numArray = append(numArray, inumber)
    }
    sort.Ints(numArray)
    for i := 0; i < len(numArray); i++ {
        if i == len(numArray)-1 {
            fmt.Print(numArray[i])
        } else {
            fmt.Printf("%d+", numArray[i])
        }
    }
}
```

### 41A.go

```text
package main

import (
    "fmt"
    "os"
)

func main() {
    var string1 string
    var string2 string
    _, _ = fmt.Scanln(&string1)
    _, _ = fmt.Scanln(&string2)

    for i:=0; i<len(string2); i++ {
        temp := len(string2) - 1 - i
        if string1[i] != string2[temp]{
            fmt.Println("NO")
            os.Exit(0)
        }
    }
    fmt.Println("YES")
}
```

### 4A.go

```text
package main

import "fmt"

func main() {
    var number uint8
    _, _ = fmt.Scanln(&number)
    if number == 2 {
        fmt.Println("NO")
    } else if number%2 == 0 {
        fmt.Println("YES")
    } else {
        fmt.Println("NO")
    }
}
```

### 58A.go

```text
package main

import (
    "fmt"
    "strings"
)

func main() {
    var istring string
    _, _ = fmt.Scan(&istring)
    var check = []string{"h","e","l","l","o"}
    j:=0
    count :=0
    temp := strings.Split(istring,"")
    for i:=0; i<len(temp); i++ {
        if temp[i] == check[j] {
            count++
            if count == 5 {
                break
            } else {
                j++
            }
        }
    }
    if count == 5 {
        fmt.Println("YES")
    } else {
        fmt.Println("NO")
    }
}
```

### 59A.go

```text
package main

import (
    "fmt"
    "strings"
)

func main() {
    var word string
    _, _ = fmt.Scanln(&word)

    lower := 0
    upper := 0

    for i:=0; i<len(word); i++ {
        if word[i] >= 65 && word[i] <= 90 {
            upper ++
        } else {
            lower++
        }
    }
    if upper > lower {
        fmt.Println(strings.ToUpper(word))
    } else  {
        fmt.Println(strings.ToLower(word))
    }
}
```

### 69A.go

```text
package main

import "fmt"

func main() {
    var num int
    _, _ = fmt.Scanln(&num)
    var twodslices = make([][3]int, num)
    for i:=0; i<num; i++ {
        for j:=0; j<3; j++ {
            _, _ = fmt.Scan(&twodslices[i][j])
        }
    }
    flag := 0
    for i:=0; i<3; i++ {
        count :=0
        for j:=0; j<num; j++ {
            count = count + twodslices[j][i]
        }
        if count != 0 {
            fmt.Println("NO")
            flag = 1
            break
        }
    }
    if flag == 0 {
        fmt.Println("YES")
    }
}
```

### 71A.go

```text
package main

import (
    "fmt"
)

func main() {
    var number uint8
    _, _ = fmt.Scanln(&number)

    for number > 0 {
        var iString string
        _, _ = fmt.Scanln(&iString)
        if len(iString) <= 10 {
            fmt.Printf("%s\n",iString)
        } else {
            length := len(iString)
            fmt.Printf("%c%d%c\n", iString[0], length-2, iString[length-1])
        }
        number--
    }
}
```

### 96A.go

```text
package main

import (
    "fmt"
    "strings"
)

func main() {
    var istring string
    fmt.Scan(&istring)
    temp := strings.Split(istring,"")
    answer := "NO"
    for i:=0;i<len(temp)-6; i++ {
        t := temp[i]
        if temp[i+1] == t && temp[i+2] == t && temp[i+3] == t && temp[i+4] == t && temp[i+5] == t && temp[i+6] == t {
            answer = "YES"
            break
        }
    }
    fmt.Println(answer)
}
```

### 1030A.go

```text
package main

import (
    "bufio"
    "fmt"
    "os"
)

var reader *bufio.Reader = bufio.NewReader(os.Stdin)

func scanf(f string, a ...interface{}) { fmt.Fscanf(reader, f, a...) }

func main() {

    var number, flag uint = 0, 0
    _, _ = fmt.Scanln(&number)
    var oned = make([]int, number, number+2)
    for i := 0; i < len(oned); i++ {
        scanf("%d", &oned[i])
        if oned[i] == 1 {
            flag = 1
        }
    }
    if flag == 0 {
        fmt.Print("EASY")
    } else {
        fmt.Print("HARD")
    }

}
```

### 344A.go

```text
package main

import (
    "bufio"
    "fmt"
    "os"
)

var reader *bufio.Reader = bufio.NewReader(os.Stdin)

func scanf(f string, a ...interface{}) { fmt.Fscanf(reader, f, a...) }

func main() {
    var number, i int = 0, 1
    _, _ = fmt.Scanln(&number)
    var oned = make([]int, number, number+3)

    if number == 1 {
        _, _ = fmt.Scanln(&oned[0])
        fmt.Print("1")
        os.Exit(0)
    }
    count := 1
    _, _ = fmt.Scanln(&oned[0])
    for i = 1; i < number; i++ {
        scanf("%d\n", &oned[i])
        if oned[i] != oned[i-1] {
            count++
        }
    }

    fmt.Println(count)

}
```

### 467A.go

```text
package main

import (
    "bufio"
    "fmt"
    "os"
)

var reader *bufio.Reader = bufio.NewReader(os.Stdin)

func scanf(f string, a ...interface{}) { fmt.Fscanf(reader, f, a...) }

func main() {
    var num uint
    _, _ = fmt.Scanln(&num)
    matrix := make([][2]uint32, num, num+3)
    var count, i uint = 0, 0
    for i = 0; i < num; i++ {
        scanf("%d %d\n", &matrix[i][0], &matrix[i][1])
        if matrix[i][0] < matrix[i][1] {
            if matrix[i][1]-matrix[i][0] >= 2 {
                count++
            }
        }
    }
    fmt.Print(count)
}
```

### 497A.go

```text
package main

import "fmt"

func main() {
    var a, b, c, flag, ans int = 0, 0, 0, 0, 0
    fmt.Scanln(&a)
    if a == 1 {
        flag = 1
    }
    fmt.Scanln(&b)
    if b == 1 {
        flag = 1
    }
    fmt.Scanln(&c)
    if c == 1 {
        flag = 1
    }
    if flag == 1 {
        ans = a * (b + c)

    } else {
        ans = a * b * c
    }
    fmt.Println(ans)
}
```

### 546A.go

```text
package main

import "fmt"

func main() {

    var cost,number, amount int32
    _, _ = fmt.Scan(&cost)
    _, _ = fmt.Scan(&amount)
    _, _ = fmt.Scan(&number)

    temp := cost*(number*(number+1))/2

    if temp - amount < 0 {
        fmt.Println("0")
    } else {
        final := temp-amount
        fmt.Println(final)
    }

}
```

### 677A.go

```text
package main

import (
    "bufio"
    "fmt"
    "os"
)

var reader *bufio.Reader = bufio.NewReader(os.Stdin)

func scanf(f string, a ...interface{}) { fmt.Fscanf(reader, f, a...) }

func main() {

    var number, height, i int16 = 0, 0, 0
    _, _ = fmt.Scan(&number)
    _, _ = fmt.Scan(&height)

    var oned = make([]int16, number, number+4)

    for i = 0; i < number; i++ {
        scanf("%d ", &oned[i])
    }

    var count int = 0
    for i = 0; i < number; i++ {
        for oned[i] > 0 {
            count++
            oned[i] = oned[i] - height
        }
    }
    fmt.Print(count)

}
```

### 734A.go

```text
package main

import (
    "bufio"
    "fmt"
    "os"
    "strings"
)

var reader *bufio.Reader = bufio.NewReader(os.Stdin)
var writer *bufio.Writer = bufio.NewWriter(os.Stdout)

func printf(f string, a ...interface{}) { fmt.Fprintf(writer, f, a...) }
func scanf(f string, a ...interface{})  { fmt.Fscanf(reader, f, a...) }

func main() {
    var num int32
    scanf("%d\n", &num)
    var xstring string
    scanf("%s\n", &xstring)
    temp := strings.Split(xstring, "")
    var a, d, i int = 0, 0, 0
    for i = 0; i < len(temp); i++ {
        if temp[i] == "A" {
            a++
        } else {
            d++
        }
    }
    if a > d {
        fmt.Println("Anton")
    } else if a < d {
        fmt.Println("Danik")
    } else {
        fmt.Println("Friendship")
    }
}
```

### 791A.go

```text
package main

import "fmt"

func main() {

    var limak,bob uint32 = 0,0
    _, _ = fmt.Scan(&limak)
    _, _ = fmt.Scan(&bob)

    var i int = 0

    for {
        i++
        limak = limak*3
        bob = bob*2
        if limak > bob {
            break
        }
    }
    fmt.Println(i)

}
```

### 977A.go

```text
package main

import "fmt"

func main() {

    var number uint32 = 0
    var k int = 0
    _, _ = fmt.Scan(&number)
    _, _ = fmt.Scan(&k)

    for i:=0; i<k; i++ {
        if number%10 !=0 {
            number--
        } else {
            number = number/10
        }
    }

    fmt.Println(number)


}
```

