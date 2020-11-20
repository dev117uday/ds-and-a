---
description: 30 days challenge hackerrank
---

# 30 days of Code

### day\_01.go

```text
package main

import (
    "bufio"
    "fmt"
    "os"
)

func main() {
    //Enter your code here. Read input from STDIN. Print output to STDOUT
    // bufio implements buffered textual I/O
    reader := bufio.NewReader(os.Stdin)
    // to read string till '\n' newline sequence.
    // .Readstring return two values : 1st the string itself and 2nd an error (if it occured else nil)
    inputString, _ := reader.ReadString('\n')
    fmt.Println("Hello, World.")
    fmt.Println(inputString)
}
```

### day\_02.go

```text
package main

import (
    "bufio"
    "fmt"
    "os"
    "strconv"
)

func main() {
    var _ = strconv.Itoa // Ignore this comment. You can still use the package "strconv".

    var i uint64 = 4
    var d float64 = 4.0
    var s string = "HackerRank "

    scanner := bufio.NewScanner(os.Stdin)
    // Declare second integer, double, and String variables.
    var num uint64
    var dec float64
    var str string
    // Read and save an integer, double, and String to your variables.
    fmt.Scanln(&num)
    fmt.Scanln(&dec)
    for scanner.Scan() {
        str = scanner.Text()
    }
    // Print the sum of both integer variables on a new line.
    fmt.Println(num + i)
    // Print the sum of the double variables on a new line.
    fmt.Printf("%.1f\n", dec+d)
    // Concatenate and print the String variables on a new line
    // The 's' variable above should be printed first.
    fmt.Println(s + str)
}
```

### day\_03.go

```text
package main

import (
    "bufio"
    "fmt"
    "io"
    "math"
    "os"
    "strconv"
    "strings"
)

// remember to import "math"

// Complete the solve function below.
func solve(meal_cost float64, tip_percent int32, tax_percent int32) {
    // calculating total according to given condition
    tip := float64(tip_percent) / 100 * meal_cost
    tax := float64(tax_percent) / 100 * meal_cost
    total := tip + tax + meal_cost
    total = math.Round(total)
    fmt.Println(total)
}

func main() {
    reader := bufio.NewReaderSize(os.Stdin, 1024*1024)

    meal_cost, err := strconv.ParseFloat(readLine(reader), 64)
    checkError(err)

    tip_percentTemp, err := strconv.ParseInt(readLine(reader), 10, 64)
    checkError(err)
    tip_percent := int32(tip_percentTemp)

    tax_percentTemp, err := strconv.ParseInt(readLine(reader), 10, 64)
    checkError(err)
    tax_percent := int32(tax_percentTemp)

    solve(meal_cost, tip_percent, tax_percent)
}

func readLine(reader *bufio.Reader) string {
    str, _, err := reader.ReadLine()
    if err == io.EOF {
        return ""
    }

    return strings.TrimRight(string(str), "\r\n")
}

func checkError(err error) {
    if err != nil {
        panic(err)
    }
}
```

### day\_04.go

```text
package main

import (
    "fmt"
)

func main() {
    //Enter your code here. Read input from STDIN. Print output to STDOUT
    var number uint32
    fmt.Scan(&number)
    // condition : If n is odd, print Weird
    if number%2 == 1 {
        fmt.Println("Weird")
    } else {
        // to apply second given condition
        if number < 6 && number > 2 {
            fmt.Println("Not Weird")
        }
        // to apply third given condition
        if number <= 20 && number > 6 {
            fmt.Println("Weird")
        }
        // to apply fourth given condition
        if number > 21 {
            fmt.Println("Not Weird")
        }
    }
}
```

### day\_05.go

```text
package main

import "fmt"

type person struct {
    age int
}

func (p person) NewPerson(initialAge int) person {
    //Add some more code to run some checks on initialAge
    // condition age cannot be below 0
    if initialAge < 0 {
        fmt.Println("Age is not valid, setting age to 0.")
        p.age = 0
    }
    return p
}

func (p person) amIOld() {
    //Do some computation in here and print out the correct statement to the console
    if p.age < 13 {
        fmt.Println("You are young.")
    } else if p.age >= 13 && p.age < 18 {
        fmt.Println("You are a teenager.")
    } else {
        fmt.Println("You are old.")
    }
}

func (p person) yearPasses() person {
    //Increment the age of the person in here
    p.age++
    return p
}

func main() {
    var T, age int

    fmt.Scan(&T)

    for i := 0; i < T; i++ {
        fmt.Scan(&age)
        p := person{age: age}
        p = p.NewPerson(age)
        p.amIOld()
        for j := 0; j < 3; j++ {
            p = p.yearPasses()
        }
        p.amIOld()
        fmt.Println()
    }
}
```

### day\_06.go

```text
package main

import (
    "bufio"
    "fmt"
    "io"
    "os"
    "strconv"
    "strings"
)

func main() {
    reader := bufio.NewReaderSize(os.Stdin, 1024*1024)

    nTemp, err := strconv.ParseInt(readLine(reader), 10, 64)
    checkError(err)
    n := int32(nTemp)
    //Printing the table using C style syntax
    var i int32
    for i = 1; i <= 10; i++ {
        fmt.Printf("%d x %d = %d\n", n, i, n*i)
    }
}

func readLine(reader *bufio.Reader) string {
    str, _, err := reader.ReadLine()
    if err == io.EOF {
        return ""
    }

    return strings.TrimRight(string(str), "\r\n")
}

func checkError(err error) {
    if err != nil {
        panic(err)
    }
}
```

### day\_07.go

```text
package main

import "fmt"

func main() {
    //Enter your code here. Read input from STDIN. Print output to STDOUT
    // reading the number of string to be given
    var numberOfString int
    fmt.Scanln(&numberOfString)

    for i := 0; i < numberOfString; i++ {
        // reading the string in same variable again and again
        var inputString string
        fmt.Scanln(&inputString)

        for x := 0; x < len(inputString); x++ {
            //printing even position charaters
            if x%2 == 0 {
                // remember to convert to string because inputString[x] returns thier ASCII code/number
                fmt.Print(string(inputString[x]))
            }
        }
        fmt.Print(" ")
        for x := 0; x < len(inputString); x++ {
            //printing odd position charaters
            if x%2 != 0 {
                fmt.Print(string(inputString[x]))
            }
        }
        fmt.Print("\n")
    }
}
```

### day\_08.go

```text
package main

import (
    "bufio"
    "fmt"
    "io"
    "os"
    "strconv"
    "strings"
)

func main() {
    reader := bufio.NewReaderSize(os.Stdin, 1024*1024)

    nTemp, err := strconv.ParseInt(readLine(reader), 10, 64)
    checkError(err)
    n := int32(nTemp)

    arrTemp := strings.Split(readLine(reader), " ")

    var arr []int32

    for i := 0; i < int(n); i++ {
        arrItemTemp, err := strconv.ParseInt(arrTemp[i], 10, 64)
        checkError(err)
        arrItem := int32(arrItemTemp)
        arr = append(arr, arrItem)
    }
    // Solution : a for loop that start from len(arr)-1 (becuz index starts from zero) till i>=0
    for i := len(arr) - 1; i >= 0; i-- {
        fmt.Print(arr[i], " ")
    }
}

func readLine(reader *bufio.Reader) string {
    str, _, err := reader.ReadLine()
    if err == io.EOF {
        return ""
    }

    return strings.TrimRight(string(str), "\r\n")
}

func checkError(err error) {
    if err != nil {
        panic(err)
    }
}
```

### day\_09.go

```text
// this challenge requires fast I/O, hence prefer to use bufio, using fmt.Scan wont work
// and will give you time limit exceed error

package main

import (
    "bufio"
    "fmt"
    "os"
)

func main() {
    //Enter your code here. Read input from STDIN. Print output to STDOUT

    var num int            // number of inputs
    var name, phone string // string for name and phone

    // make() is used to create variables on heap
    // here we create a map of [string]string
    phoneBook := make(map[string]string)

    scanner := bufio.NewScanner(os.Stdin)

    fmt.Scanln(&num)
    for i := 0; i < num; i++ {
        fmt.Scanf("%s %s", &name, &phone)
        phoneBook[name] = phone
    }

    for scanner.Scan() {
        str := scanner.Text()
        // when accessing a map, it return 2 things, the value and a boolean telling whether it exist or not
        // we dont need the value right not, just needs the boolean, so we can use '_' in it's place
        _, answer := phoneBook[str]
        if answer == true {
            fmt.Printf("%s=%s\n", str, phoneBook[str])
        } else {
            fmt.Printf("Not found\n")
        }
    }

}
```

### day\_10.go

```text
package main

import (
    "bufio"
    "fmt"
    "io"
    "os"
    "strconv"
    "strings"
)

// Complete the factorial function below.
func factorial(n int32) int32 {
    // handling edges cases
    if n == 0 || n == 1 {
        return 1
    }
    // initializing with 1 becuase by default it gets initialized with 0
    var factorial int32 = 1
    // using loop to calculate factorial
    for n > 0 {
        factorial = factorial * n
        n--
    }
    return factorial
}

func main() {
    reader := bufio.NewReaderSize(os.Stdin, 1024*1024)

    stdout, err := os.Create(os.Getenv("OUTPUT_PATH"))
    checkError(err)

    defer stdout.Close()

    writer := bufio.NewWriterSize(stdout, 1024*1024)

    nTemp, err := strconv.ParseInt(readLine(reader), 10, 64)
    checkError(err)
    n := int32(nTemp)

    result := factorial(n)

    fmt.Fprintf(writer, "%d\n", result)

    writer.Flush()
}

func readLine(reader *bufio.Reader) string {
    str, _, err := reader.ReadLine()
    if err == io.EOF {
        return ""
    }

    return strings.TrimRight(string(str), "\r\n")
}

func checkError(err error) {
    if err != nil {
        panic(err)
    }
}
```

### day\_11.go

```text
package main

import (
    "bufio"
    "fmt"
    "io"
    "os"
    "strconv"
    "strings"
)

func main() {
    reader := bufio.NewReaderSize(os.Stdin, 1024*1024)

    nTemp, err := strconv.ParseInt(readLine(reader), 10, 64)
    checkError(err)
    n := int32(nTemp)
    // to convert the number to binary, use %b with fmt.Sprint, it return the binary number as a string
    binaryString := fmt.Sprintf("%b", n)
    // to iterate over the binary string
    counter := 0
    maxString := 0
    for _, value := range binaryString {
        if string(value) == "1" {
            counter++
        } else {
            // if the maxstring of "1" is less than the current counter of maxstring
            // then make the maxstring = current mex length of  "1"
            if maxString < counter {
                maxString = counter
            }
            // reseting becuase if in-countered a 0
            counter = 0
        }
    }

    if counter > maxString {
        fmt.Println(counter)
    } else {
        fmt.Println(maxString)
    }
}

func readLine(reader *bufio.Reader) string {
    str, _, err := reader.ReadLine()
    if err == io.EOF {
        return ""
    }

    return strings.TrimRight(string(str), "\r\n")
}

func checkError(err error) {
    if err != nil {
        panic(err)
    }
}
```

### day\_12.go

```text
package main

import (
    "bufio"
    "fmt"
    "io"
    "os"
    "strconv"
    "strings"
)

// Go by defualt doesnt have min max int's, so this is a work around :|
const maxInt = int(^uint(0) >> 1)
const minInt = -maxInt - 1

func main() {
    reader := bufio.NewReaderSize(os.Stdin, 1024*1024)

    var arr [][]int32
    for i := 0; i < 6; i++ {
        arrRowTemp := strings.Split(readLine(reader), " ")

        var arrRow []int32
        for _, arrRowItem := range arrRowTemp {
            arrItemTemp, err := strconv.ParseInt(arrRowItem, 10, 64)
            checkError(err)
            arrItem := int32(arrItemTemp)
            arrRow = append(arrRow, arrItem)
        }

        if len(arrRow) != int(6) {
            panic("Bad input")
        }

        arr = append(arr, arrRow)
    }

    max := minInt
    for i := 0; i < 4; i++ {
        for j := 0; j < 4; j++ {
            a := arr[i][j] + arr[i][j+1] + arr[i][j+2]
            b := arr[i+1][j+1]
            c := arr[i+2][j] + arr[i+2][j+1] + arr[i+2][j+2]
            if max < int(a+b+c) {
                max = int(a + b + c)
            }
        }
    }
    fmt.Println(max)
}

func readLine(reader *bufio.Reader) string {
    str, _, err := reader.ReadLine()
    if err == io.EOF {
        return ""
    }

    return strings.TrimRight(string(str), "\r\n")
}

func checkError(err error) {
    if err != nil {
        panic(err)
    }
}
```

### day\_13.go

```text
// Golang doesnt have inheritance thats why
// hackerRank doesnt have Golang as a option in this challenge
// so please try in some other language to solve it

package day12
```

### day\_14.go

```text
// Golang doesnt have abstract classes
// hackerRank doesnt have Golang as a option in this challenge
// so please try in some other language to solve it

package day13
```

### day\_15.go

```text
package main

import "fmt"

func main() {
    var a []int = []int{}
    var i, j, e, n int

    fmt.Scan(&n)

    for i = 0; i < n; i++ {
        fmt.Scan(&e)
        a = append(a, e)
    }

    totalSwaps := 0

    for i = 0; i < n; i++ {
        numberOfSwaps := 0

        for j = 0; j < n-1; j++ {
            if a[j] > a[j+1] {
                a[j], a[j+1] = a[j+1], a[j]
                numberOfSwaps++
                totalSwaps++
            }
        }

        if numberOfSwaps == 0 {
            break
        }
    }

    fmt.Printf("Array is sorted in %d swaps.\n", totalSwaps)
    fmt.Printf("First Element: %d\n", a[0])
    fmt.Printf("Last Element: %d\n", a[len(a)-1])
}
```

### day\_16.go

```text
package main

import (
    "fmt"
)

func main() {
    var numbers int
    var number int
    fmt.Scanln(&numbers)
    for i := 0; i < numbers; i++ {
        fmt.Scanln(&number)
        isPrime := true
        if number <= 1 {
            fmt.Println("Not prime")
        } else if number <= 3 {
            fmt.Println("Prime")
        } else if number%3 == 0 || number%2 == 0 {
            fmt.Println("Not prime")
        } else {
            for i := 5; i*i <= number; i = i + 1 {
                if number%i == 0 {
                    fmt.Println("Not prime")
                    isPrime = false
                    break
                }
            }
            if isPrime == true {
                fmt.Println("Prime")
            }
        }
    }
}
```

### day\_17.go

```text
package main

import "fmt"

func main() {
    var y1, y2, m1, m2, d1, d2 int
    fmt.Scanln(&d2, &m2, &y2)
    fmt.Scanln(&d1, &m1, &y1)

    if y2 > y1 {
        fmt.Print(10000)
    } else if m2 > m1 && y2 == y1 {
        fmt.Print(500 * (m2 - m1))
    } else if d2 > d1 && m2 == m1 && y2 == y1 {
        fmt.Print(15 * (d2 - d1))
    } else {
        fmt.Print(0)
    }

}
```

### day\_18.go

```text
package main

import (
    "bufio"
    "fmt"
    "io"
    "os"
    "sort"
    "strconv"
    "strings"
)

func main() {
    reader := bufio.NewReaderSize(os.Stdin, 1024*1024)

    NTemp, err := strconv.ParseInt(readLine(reader), 10, 64)
    checkError(err)
    N := int32(NTemp)
    var names []string
    for NItr := 0; NItr < int(N); NItr++ {
        firstNameEmailID := strings.Split(readLine(reader), " ")

        firstName := firstNameEmailID[0]

        emailID := firstNameEmailID[1]
        i := 0
        n := len(emailID)
        for i < n && emailID[i] != '@' {
            i++
        }

        if i+6 < n && emailID[i+1:i+6] == "gmail" && i+10 <= n && emailID[i+7:i+10] == "com" {
            names = append(names, firstName)
        }
    }
    sort.Strings(names)
    for i := 0; i < len(names); i++ {
        fmt.Println(names[i])
    }
}

func readLine(reader *bufio.Reader) string {
    str, _, err := reader.ReadLine()
    if err == io.EOF {
        return ""
    }

    return strings.TrimRight(string(str), "\r\n")
}

func checkError(err error) {
    if err != nil {
        panic(err)
    }
}
```

### day\_19.go

```text
package main

import (
    "bufio"
    "fmt"
    "io"
    "os"
    "strconv"
    "strings"
)

func main() {
    reader := bufio.NewReaderSize(os.Stdin, 1024*1024)

    tTemp, err := strconv.ParseInt(readLine(reader), 10, 64)
    checkError(err)
    t := int32(tTemp)

    for tItr := 0; tItr < int(t); tItr++ {
        nk := strings.Split(readLine(reader), " ")

        nTemp, err := strconv.ParseInt(nk[0], 10, 64)
        checkError(err)
        n := int32(nTemp)

        kTemp, err := strconv.ParseInt(nk[1], 10, 64)
        checkError(err)
        k := int32(kTemp)
        var res int32
        if ((k - 1) | k) <= n {
            res = k - 1
        } else {
            res = k - 2
        }
        fmt.Println(res)
    }
}

func readLine(reader *bufio.Reader) string {
    str, _, err := reader.ReadLine()
    if err == io.EOF {
        return ""
    }

    return strings.TrimRight(string(str), "\r\n")
}

func checkError(err error) {
    if err != nil {
        panic(err)
    }
}
```

