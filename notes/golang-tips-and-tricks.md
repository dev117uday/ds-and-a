---
description: Tips & Tricks
---

# Golang Tips & Tricks

## Logics in go

### Min/Max Int and Uint

```text
const MaxUint = ^uint(0)
const MinUint = 0

const MaxInt = int(^uint(0) >> 1)
const MinInt = -MaxInt - 1
```

