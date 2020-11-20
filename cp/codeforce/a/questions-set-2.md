---
description: Cpp
---

# Questions \(Set 2\)

### 158B.cpp

```text
#include <stdio.h>

using namespace std;

int main()
{
    int n, s, count[5]= {0};
    scanf("%d", &n);
    while (n--)
    {
        scanf("%d", &s);
        count[s] += 1;
    }
    int total = count[4] + count[3] + count[2] / 2;
    count[1] -= count[3];
    if (count[2] % 2 == 1)
    {
        total += 1;
        count[1] -= 2;
    }
    if (count[1] > 0)
    {
        total += (count[1] + 3) / 4;
    }
    printf("%d\n", total);
    return 0;
}
```

### 1A.cpp

```text
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

### 266B.cpp

```text
#include <iostream>
#include <string>

using namespace std;

int main()
{
    int n, t;
    string s;
    cin >> n >> t >> s;
    while (t--)
    {
        for (int i = 1; i < n; ++i)
        {
            if (s[i] == 'G' && s[i-1] == 'B')
            {
                s[i] = 'B';
                s[i-1] = 'G';
                ++i;
            }
        }
    }
    cout << s << endl;
    return 0;
}
```

### 344A.cpp

```text
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

### 4A.cpp

```text
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

### 71A.cpp

```text
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

