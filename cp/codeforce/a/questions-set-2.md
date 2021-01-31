---
description: Codeforce A
---

# Questions \(Set 2\)

## 1A.cpp

```cpp
#include <iostream>
#include <cmath>

using namespace std;

int main(){
    unsigned long long width,height,flagstone;
    cin>> width;
    cin>>height;
    cin>>flagstone;
    unsigned long long answer = ceil((double)width/flagstone)*ceil((double)height/flagstone);
    cout << answer;
}
```

## 344A.cpp

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {

    unsigned int number = 0;
    cin >> number ;
    vector<unsigned short int> vector1 (number);

    if(number == 1){
        cin >> vector1[0];
        cout << "1";
        exit(0);
    }
    unsigned int count = 1;
    cin >> vector1[0];
    for (unsigned int i=1; i<number; i++) {
        cin >> vector1[i];
        if(vector1[i] != vector1[i-1]){
            count += 1;
        }
    }
    cout << count;
}
```

## 4A.cpp

```cpp
#include <iostream>

using namespace std;

int main(){

    unsigned short int weight = 0;

    cin >> weight;

    if(weight == 2){
        cout << "NO" << "\n";
    } else if (weight%2==0){
        cout << "YES" << "\n";
    } else {
        cout << "NO" << "\n";
    }

    return 0;
}
```

## 71A.cpp

```cpp
#include <iostream>

using namespace std;

int main()
{
    unsigned short int n=0;
    string xstr;
    cin >> n;
    while (n--)
    {
        cin >> xstr;
        if (xstr.length() > 10)
        {
            cout << xstr[0] << xstr.length() - 2 << xstr[xstr.length() - 1] << endl;
        }
        else
        {
            cout << xstr << endl;
        }
    }
    return 0;
}
```

## 131A.go

```go
package main

import (
    "fmt"
    "strings"
)

func main() {

    var inputString string
    _, _ = fmt.Scanln(&inputString)
    magic(inputString)

}

func magic(inputString string) {
    if allUpper(inputString) {
        fmt.Print(strings.ToLower(inputString))
        return
    }
    if isSpecialCase(inputString) {
        str := string(inputString[0]-32) + (strings.ToLower(inputString[1:]))
        fmt.Print(str)
    } else {
        fmt.Print(inputString)
    }
}

func allUpper(input string) bool {
    for _, val := range input {
        if val >= 65 && val <= 90 {
            continue
        } else {
            return false
        }
    }
    return true
}

func isSpecialCase(input string) bool {
    if input[0] >= 97 && input[0] <= 122 {
        for i := 1; i < len(input); i++ {
            if input[i] >= 65 && input[i] <= 90 {
                continue
            } else {
                return false
            }
        }
    } else {
        return false
    }
    return true
}
```

