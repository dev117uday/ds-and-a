---
description: Imp Stuff
---

# Theory

## Tail recursion

The tail recursion is better than non-tail recursion. As there is no task left after the recursive call, it will be easier for the compiler to optimize the code. When one function is called, its address is stored inside the stack. So if it is tail recursion, then storing addresses into stack is not needed.

We can use factorial using recursion, but the function is not tail recursive. The value of fact\(n-1\) is used inside the fact\(n\).

```text
long fact(int n){
   if(n <= 1)
      return 1;
   n * fact(n-1);
}
```

We can make it tail recursive, by adding some other parameters. This is like below −

```text
long fact(long n, long a){
   if(n == 0)
      return a;
   return fact(n-1, a*n);
}
```

