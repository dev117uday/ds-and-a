---
description: Linkedlist
---

# Golang

### breadth-first.go

```go
package main

import "fmt"

type tree struct {
    key   int
    left  *tree
    right *tree
}

func printTreeInorder(root *tree) {
    if root == nil {
        return
    }
    printTreeInorder(root.left)
    fmt.Println(root.key)
    printTreeInorder(root.right)
}

func levelOrder(root *tree) {

    if root == nil {
        return
    }

    queue := []tree{*root}
    for len(queue) != 0 {
        node := queue[0]
        fmt.Print(node.key, " ")
        if node.left != nil {
            queue = append(queue, *node.left)
        }
        if node.right != nil {
            queue = append(queue, *node.right)
        }
        queue = queue[1:]
        fmt.Println(" ")
    }

}

func main() {

    root := &tree{key: 10, left: nil, right: nil}
    root.left = &tree{key: 20, left: nil, right: nil}
    root.left.left = &tree{key: 100, left: nil, right: nil}
    root.right = &tree{key: 30, left: nil, right: nil}
    root.right.right = &tree{key: 40, left: nil, right: nil}
    root.right.left = &tree{key: 70, left: nil, right: nil}
    root.right.right.right = &tree{key: 50, left: nil, right: nil}
    root.right.right.right.right = &tree{key: 60, left: nil, right: nil}

    // fmt.Println("In-order")
    // printTreeInorder(root)

    levelOrder(root)

}
```

### bst.go

```go
package main

import "fmt"

type tree struct {
    key   int
    left  *tree
    right *tree
}

func printTreeInorder(root *tree) {
    if root == nil {
        return
    }
    printTreeInorder(root.left)
    fmt.Println(root.key)
    printTreeInorder(root.right)
}

func printTreePreorder(root *tree) {
    if root == nil {
        return
    }
    fmt.Println(root.key)
    printTreePreorder(root.left)
    printTreePreorder(root.right)
}

func printTreePostorder(root *tree) {
    if root == nil {
        return
    }
    printTreePreorder(root.left)
    printTreePreorder(root.right)
    fmt.Println(root.key)
}

func main() {

    root := &tree{key: 10, left: nil, right: nil}
    root.left = &tree{key: 20, left: nil, right: nil}
    root.right = &tree{key: 30, left: nil, right: nil}

    fmt.Println("In-order")
    printTreeInorder(root)
    fmt.Println("Pre-order")
    printTreePreorder(root)
    fmt.Println("Post-order")
    printTreePostorder(root)
}
```

### bsttodll.go

```go
package main

import "fmt"

type tree struct {
    key   int
    left  *tree
    right *tree
}

var prev *tree

func printDLL(head *tree) {
    temp := head
    for temp != nil {
        fmt.Println(temp.key)
        temp = temp.right
    }
}

func bstTodll(root *tree) *tree {

    if root == nil {
        return root
    }
    head := bstTodll(root.left)
    if prev == nil {
        head = root
    } else {
        root.left = prev
        prev.right = root
    }
    prev = root
    bstTodll(root.right)
    return head

}

func main() {

    var root = newTreeNode(10)
    root.left = newTreeNode(20)
    root.right = newTreeNode(30)
    root.right.left = newTreeNode(40)
    root.right.right = newTreeNode(50)

    temp := bstTodll(root)
    printDLL(temp)

}

func newTreeNode(number int) *tree {
    return &tree{key: number, left: nil, right: nil}
}
```

### checkBalance.go

```go
package main

import (
    "fmt"
    "math"
)

type tree struct {
    key   int
    left  *tree
    right *tree
}

func max(a, b int) int {
    if a > b {
        return a
    }
    return b
}

func checkbalance(root *tree) int {

    if root == nil {
        return 0
    }
    ltree := checkbalance(root.left)
    if ltree == -1 {
        return -1
    }
    rtree := checkbalance(root.right)
    if rtree == -1 {
        return -1
    }
    if int(math.Abs(float64(ltree-rtree))) > 1 {
        return -1
    } else {
        return max(ltree, rtree) + 1
    }

}

func main() {

    root := &tree{key: 30, left: nil, right: nil}
    root.left = &tree{key: 10, left: nil, right: nil}
    root.left.left = &tree{key: 10, left: nil, right: nil}
    root.left.left.left = &tree{key: 10, left: nil, right: nil}
    root.right = &tree{key: 20, left: nil, right: nil}
    root.right.right = &tree{key: 30, left: nil, right: nil}
    root.right.left = &tree{key: 30, left: nil, right: nil}
    // fmt.Println("In-order")

    fmt.Println(checkbalance(root))

}
```

### child sum property.go

```go
package main

import "fmt"

type tree struct {
    key   int
    left  *tree
    right *tree
}

func csp(root *tree) bool {

    if root == nil {
        return true
    }
    if root.left == nil && root.right == nil {
        return true
    }
    sum := 0
    if root.right != nil {
        sum += root.left.key
    }
    if root.left != nil {
        sum += root.right.key
    }

    return (root.key == sum) && csp(root.left) && csp(root.right)

}

func main() {

    root := &tree{key: 30, left: nil, right: nil}
    root.left = &tree{key: 10, left: nil, right: nil}
    root.right = &tree{key: 20, left: nil, right: nil}

    // fmt.Println("In-order")

    fmt.Println(csp(root))

}
```

### height-bst.go

```go
package main

import "fmt"

type tree struct {
    key   int
    left  *tree
    right *tree
}

func printTreeInorder(root *tree) {
    if root == nil {
        return
    }
    printTreeInorder(root.left)
    fmt.Println(root.key)
    printTreeInorder(root.right)
}

func heightOfTree(root *tree) int {

    if root == nil {
        return 0
    }
    return max(heightOfTree(root.left), heightOfTree(root.right)) + 1
}

func max(a, b int) int {
    if a > b {
        return a
    }
    return b
}

func main() {

    root := &tree{key: 10, left: nil, right: nil}
    root.left = &tree{key: 20, left: nil, right: nil}
    root.right = &tree{key: 30, left: nil, right: nil}
    root.right.right = &tree{key: 40, left: nil, right: nil}
    root.right.right.right = &tree{key: 50, left: nil, right: nil}
    root.right.right.right.right = &tree{key: 60, left: nil, right: nil}

    fmt.Println("In-order")
    printTreeInorder(root)

    fmt.Println(heightOfTree(root))

}
```

### k-distance.go

```go
package main

import "fmt"

type tree struct {
    key   int
    left  *tree
    right *tree
}

func printTreeInorder(root *tree) {
    if root == nil {
        return
    }
    printTreeInorder(root.left)
    fmt.Println(root.key)
    printTreeInorder(root.right)
}

func kDistance(root *tree, number int) {

    if root == nil {
        return
    }
    if number == 0 {
        fmt.Println(root.key)
    } else {
        kDistance(root.left, number-1)
        kDistance(root.right, number-1)
    }

}

func main() {

    root := &tree{key: 10, left: nil, right: nil}
    root.left = &tree{key: 20, left: nil, right: nil}
    root.right = &tree{key: 30, left: nil, right: nil}
    root.right.right = &tree{key: 40, left: nil, right: nil}
    root.right.right.right = &tree{key: 50, left: nil, right: nil}
    root.right.right.right.right = &tree{key: 60, left: nil, right: nil}

    // fmt.Println("In-order")
    // printTreeInorder(root)

    kDistance(root, 3)

}
```

### leftViewTree.go

```go
package main

import "fmt"

type tree struct {
    key   int
    left  *tree
    right *tree
}

var maxlevel int = 0

func leftView(root *tree, level int) {
    if root == nil {
        return
    }

    if maxlevel < level {
        fmt.Print(root.key, " | ")
        maxlevel = level
    }

    leftView(root.left, level+1)
    leftView(root.right, level+1)
}

func main() {

    root := &tree{key: 10, left: nil, right: nil}
    root.left = &tree{key: 20, left: nil, right: nil}
    root.right = &tree{key: 30, left: nil, right: nil}
    root.right.right = &tree{key: 40, left: nil, right: nil}
    root.right.right.right = &tree{key: 50, left: nil, right: nil}
    root.right.right.right.right = &tree{key: 60, left: nil, right: nil}

    // fmt.Println("In-order")
    leftView(root, 1)

}
```

### lot-line.go

```go
package main

import "fmt"

type tree struct {
    key   int
    left  *tree
    right *tree
}

func printTreeInorder(root *tree) {
    if root == nil {
        return
    }
    printTreeInorder(root.left)
    fmt.Println(root.key)
    printTreeInorder(root.right)
}

func levelOrder(root *tree) {

    if root == nil {
        return
    }

    queue := []tree{*root}

    for len(queue) != 0 {
        size := len(queue)
        for i := 0; i < size; i++ {
            node := queue[0]
            fmt.Print(node.key, " ")
            if node.left != nil {
                queue = append(queue, *node.left)
            }
            if node.right != nil {
                queue = append(queue, *node.right)
            }

            queue = queue[1:]
        }
    }

}

func main() {

    root := &tree{key: 10, left: nil, right: nil}
    root.left = &tree{key: 20, left: nil, right: nil}
    root.left.left = &tree{key: 100, left: nil, right: nil}
    root.right = &tree{key: 30, left: nil, right: nil}
    root.right.right = &tree{key: 40, left: nil, right: nil}
    root.right.left = &tree{key: 70, left: nil, right: nil}
    root.right.right.right = &tree{key: 50, left: nil, right: nil}
    root.right.right.right.right = &tree{key: 60, left: nil, right: nil}

    // fmt.Println("In-order")
    // printTreeInorder(root)

    levelOrder(root)

}
```

### maxValtree.go

```go
package main

import "fmt"

const MaxInt = int(^uint(0) >> 1)
const MinInt = -MaxInt - 1

type tree struct {
    key   int
    left  *tree
    right *tree
}

func printTreeInorder(root *tree) {
    if root == nil {
        return
    }
    printTreeInorder(root.left)
    fmt.Println(root.key)
    printTreeInorder(root.right)
}

func maxValTree(root *tree) int {

    if root == nil {
        return MinInt
    }

    return max(root.key, max(maxValTree(root.left), maxValTree(root.right)))

}

func max(a, b int) int {
    if a > b {
        return a
    }
    return b
}

func main() {

    root := &tree{key: 10, left: nil, right: nil}
    root.left = &tree{key: 20, left: nil, right: nil}
    root.right = &tree{key: 30, left: nil, right: nil}
    root.left.left = &tree{key: 100, left: nil, right: nil}
    root.right.right = &tree{key: 40, left: nil, right: nil}
    root.right.right.right = &tree{key: 50, left: nil, right: nil}
    root.right.right.right.right = &tree{key: 60, left: nil, right: nil}

    // fmt.Println("In-order")
    // printTreeInorder(root)

    fmt.Println(maxValTree(root))

}
```

### rightViewtree.go

```go
package main

import "fmt"

type tree struct {
    key   int
    left  *tree
    right *tree
}

var maxlevel int = 0

func rightView(root *tree, level int) {

    if root == nil {
        return
    }

    if maxlevel < level {
        fmt.Print(root.key, " | ")
        maxlevel = level
    }
    rightView(root.right, level+1)
    rightView(root.left, level+1)

}

func main() {

    root := &tree{key: 10, left: nil, right: nil}
    root.left = &tree{key: 20, left: nil, right: nil}
    root.right = &tree{key: 30, left: nil, right: nil}
    root.right.right = &tree{key: 40, left: nil, right: nil}
    root.right.right.right = &tree{key: 50, left: nil, right: nil}
    root.right.right.right.right = &tree{key: 60, left: nil, right: nil}

    // fmt.Println("In-order")
    rightView(root, 1)
    fmt.Println()

}
```

### sizeoftree.go

```go
package main

import "fmt"

type tree struct {
    key   int
    left  *tree
    right *tree
}

func printTreeInorder(root *tree) {
    if root == nil {
        return
    }
    printTreeInorder(root.left)
    fmt.Println(root.key)
    printTreeInorder(root.right)
}

func getSizeofTree(root *tree) int {

    if root == nil {
        return 0
    }
    return getSizeofTree(root.left) + getSizeofTree(root.right) + 1

}

func main() {

    root := &tree{key: 10, left: nil, right: nil}
    root.left = &tree{key: 20, left: nil, right: nil}
    root.right = &tree{key: 30, left: nil, right: nil}
    root.right.right = &tree{key: 40, left: nil, right: nil}
    root.right.right.right = &tree{key: 50, left: nil, right: nil}
    root.right.right.right.right = &tree{key: 60, left: nil, right: nil}

    // fmt.Println("In-order")
    // printTreeInorder(root)

    fmt.Println(getSizeofTree(root))

}
```

#### Max width of tree

```go
package main

import (
	"fmt"
)

type tree struct {
	key   int
	left  *tree
	right *tree
}

func max(a, b int) int {
	if a > b {
		return a
	}
	return b
}

func maxwidth(root *tree) int {
	if root == nil {
		return 0
	}
	l := []*tree{root}
	result := 0
	for len(l) != 0 {
		count := len(l)
		result = max(count, result)
		for i := 0; i < count; i++ {
			temp := l[0]
			if temp.left != nil {
				l = append(l, temp.left)
			}
			if temp.right != nil {
				l = append(l, temp.right)
			}
			l = l[1:]
		}
		fmt.Println(l)
	}
	return result
}

func main() {

	root := &tree{key: 10, left: nil, right: nil}
	root.left = &tree{key: 20, left: nil, right: nil}
	root.left.left = &tree{key: 40, left: nil, right: nil}
	root.left.right = &tree{key: 50, left: nil, right: nil}
	root.right = &tree{key: 30, left: nil, right: nil}
	root.right.left = &tree{key: 60, left: nil, right: nil}
	// fmt.Println("In-order")

	fmt.Println(maxwidth(root))

}

```



