# C\#

### breadth-first.cs

```text
using System;
using System.Collections.Generic;

namespace csharp_ide
{
    public class Tree 
    {   
        public int key;
        public Tree left;
        public Tree right;
        public Tree(int number)
        {
            key = number;
            left = null;
            right = null;
        }
    }
    class Program
    {
        public static void levelOrder(Tree root)
        {
            if (root == null)
            {
                return;
            } 
            Queue<Tree> q = new Queue<Tree>();
            q.Enqueue(root);
            while (q.Count != 0){
                var node = q.Dequeue();
                Console.WriteLine(node.key);
                if (node.left != null)
                {
                    q.Enqueue(node.left);
                }
                if (node.right != null)
                {
                    q.Enqueue(node.right);
                }
            }

        }
        static void Main(string[] args)
        {
            Tree root = new Tree(10);
            root.left = new Tree(20);
            root.right = new Tree(30);
            root.right.left = new Tree(40);
            root.right.right = new Tree(50);
            levelOrder(root);
        }
    }
}
```

### bstToDll.cs

```text
using System;
using System.Collections.Generic;

namespace csharp_ide
{
    public class Tree 
    {   
        public int key;
        public Tree left;
        public Tree right;
        public Tree(int number)
        {
            key = number;
            left = null;
            right = null;
        }
    }
    class Program
    {
        static Tree prev = null;

        public static Tree bstToDll(Tree root)
        {
            if (root == null)
                return root;

            Tree head = bstToDll(root.left) ;
            if (prev == null)
                head = root;
            else {
                root.left = prev;
                prev.right = root;
            }
            prev = root;
            bstToDll(root.right);
            return head;
        }

        static void printDLL(Tree root)
        {
            Tree temp = root;
            while(temp!= null)
            {
                Console.WriteLine(temp.key);
                temp = temp.right;
            }
        }

        static void Main(string[] args)
        {
            Tree root = new Tree(10);
            root.left = new Tree(20);
            root.right = new Tree(30);
            root.right.left = new Tree(40);
            root.right.right = new Tree(50);

            var temp = bstToDll(root);
            printDLL(temp);
        }
    }
}
```

### checkBalance.cs

```text
using System;
using System.Collections.Generic;

namespace csharp_ide
{
    public class Tree 
    {   
        public int key;
        public Tree left;
        public Tree right;
        public Tree(int number)
        {
            key = number;
            left = null;
            right = null;
        }
    }
    class Program
    {
        public static int max(int a, int b) {
            if(a>b){
                return a;
            }
            return b;
        }
        public static int checkbalance(Tree root)
        {
            if (root == null) {
                return 0;
            }   
            int ltree = checkbalance(root.left);
            if (ltree == -1) {
                return -1;
            }
            int rtree = checkbalance(root.right);
            if( rtree == -1) {
                return -1;
            }
            if (Math.Abs(ltree-rtree) > 1) {
                return -1;
            } else {
                return max(ltree,rtree)+1;
            }
        }

        static void Main(string[] args)
        {
            Tree root = new Tree(10);
            root.left = new Tree(20);
            root.right = new Tree(30);
            root.right.left = new Tree(40);
            root.right.right = new Tree(50);

            Console.WriteLine(checkbalance(root));
        }
    }
}
```

### heightBst.cs

```text
using System;
using System.Collections.Generic;

namespace csharp_ide
{
    public class Tree 
    {   
        public int key;
        public Tree left;
        public Tree right;
        public Tree(int number)
        {
            key = number;
            left = null;
            right = null;
        }
    }
    class Program
    {
        public static int max(int a, int b) {
            if(a>b){
                return a;
            }
            return b;
        }
        public static int heightOfBst(Tree root)
        {
            if (root == null){
                return 0;
            }
            return max(heightOfBst(root.left),heightOfBst(root.right))+1;

        }
        static void Main(string[] args)
        {
            Tree root = new Tree(10);
            root.left = new Tree(20);
            root.right = new Tree(30);
            root.right.left = new Tree(40);
            root.right.right = new Tree(50);

            Console.WriteLine(heightOfBst(root));
        }
    }
}
```

### inorderIter.cs

```text
using System;
using System.Collections.Generic;

namespace csharp_ide
{
    public class Tree 
    {   
        public int key;
        public Tree left;
        public Tree right;
        public Tree(int number)
        {
            key = number;
            left = null;
            right = null;
        }
    }
    class Program
    {
        public static int max(int a, int b) {
            if(a>b){
                return a;
            }
            return b;
        }
        public static void inorder(Tree root)
        {
            if (root == null)
            {
                return;
            }

            Stack<Tree> s = new Stack<Tree>();
            Tree current = root;
            while(current != null || s.Count > 0)
            {
                while(current != null)
                {
                    s.Push(current);
                    current = current.left;
                }
                current = s.Pop();
                Console.WriteLine(current.key);
                current = current.right;
            }
        }

        static void Main(string[] args)
        {
            Tree root = new Tree(10);
            root.left = new Tree(20);
            root.right = new Tree(30);
            root.right.left = new Tree(40);
            root.right.right = new Tree(50);

            inorder(root);
        }
    }
}
```

### kdistance.cs

```text
using System;
using System.Collections.Generic;

namespace csharp_ide
{
    public class Tree 
    {   
        public int key;
        public Tree left;
        public Tree right;
        public Tree(int number)
        {
            key = number;
            left = null;
            right = null;
        }
    }
    class Program
    {
        public static int max(int a, int b) {
            if(a>b){
                return a;
            }
            return b;
        }
        public static void kDistance(Tree root,int level)
        {
            if(root == null) {
                return;
            }   
            if (level == 0) {
                Console.WriteLine(root.key);
            }
            kDistance(root.left,level-1);
            kDistance(root.right,level-1);
        }
        static void Main(string[] args)
        {
            Tree root = new Tree(10);
            root.left = new Tree(20);
            root.right = new Tree(30);
            root.right.left = new Tree(40);
            root.right.right = new Tree(50);

            kDistance(root,2);
        }
    }
}
```

### leftViewTree.cs

```text
using System;
using System.Collections.Generic;

namespace csharp_ide
{
    public class Tree 
    {   
        public int key;
        public Tree left;
        public Tree right;
        public Tree(int number)
        {
            key = number;
            left = null;
            right = null;
        }
    }
    class Program
    {
        static int maxLevel = 0;
        public static int max(int a, int b) {
            if(a>b){
                return a;
            }
            return b;
        }
        public static void leftViewTree(Tree root,int level)
        {
            if (root == null) {
                return;
            }   
            if (maxLevel <level){
                Console.WriteLine(root.key);
                maxLevel = level;
            }
            leftViewTree(root.left,level+1);
            leftViewTree(root.right,level+1);

        }
        static void Main(string[] args)
        {
            Tree root = new Tree(10);
            root.left = new Tree(20);
            root.right = new Tree(30);
            root.right.left = new Tree(40);
            root.right.right = new Tree(50);

            leftViewTree(root,1);
        }
    }
}
```

### maxValTree.cs

```text
using System;
using System.Collections.Generic;

namespace csharp_ide
{
    public class Tree 
    {   
        public int key;
        public Tree left;
        public Tree right;
        public Tree(int number)
        {
            key = number;
            left = null;
            right = null;
        }
    }
    class Program
    {
        public static int max(int a, int b) {
            if(a>b){
                return a;
            }
            return b;
        }
        public static int maxValTree(Tree root)
        {
            if (root == null) {
                return int.MinValue;
            }
            return max(root.key,max(maxValTree(root.left),maxValTree(root.right)));
        }

        static void Main(string[] args)
        {
            Tree root = new Tree(10);
            root.left = new Tree(20);
            root.right = new Tree(30);
            root.right.left = new Tree(40);
            root.right.right = new Tree(50);

            Console.WriteLine(maxValTree(root));
        }
    }
}
```

### maxWidth.cs

```text
using System;
using System.Collections.Generic;

class Tree
{
    public int key;
    public Tree left;
    public Tree right;

    public Tree(int number)
    {
        key = number;
        left = null;
        right = null;
    }

}

class Program
{
    public static void Main()
    {
        Tree root = new Tree(10);
        root.right = new Tree(20);
        root.left = new Tree(30);
        root.right.right = new Tree(40);
        root.right.left = new Tree(50);
        root.left.right = new Tree(60);
        root.left.left = new Tree(70);
        Console.WriteLine(maxWidth(root));
    }
    static int maxWidth(Tree root)
    {
        if (root == null )
            return 0;

        Queue<Tree> q = new Queue<Tree>();
        q.Enqueue(root);
        int width = 0;

        while (q.Count != 0) 
        {
            int size = q.Count;
            width = Math.Max(width,size);

            while (size-- > 0 )
            {
                Tree node = q.Dequeue();
                if (node.left != null)
                {
                    q.Enqueue(node.left);
                }
                if (node.right != null)
                {
                    q.Enqueue(node.right);
                }
            }
        }
        return width;
    }
}
```

### sizeOfBST.cs

```text
using System;
using System.Collections.Generic;

namespace csharp_ide
{
    public class Tree 
    {   
        public int key;
        public Tree left;
        public Tree right;
        public Tree(int number)
        {
            key = number;
            left = null;
            right = null;
        }
    }
    class Program
    {
        public static int max(int a, int b) {
            if(a>b){
                return a;
            }
            return b;
        }
        public static int TreeSize(Tree root)
        {
            if (root == null)
            {
                return 0;
            }

            return 1+TreeSize(root.left)+TreeSize(root.right) ;
        }

        static void Main(string[] args)
        {
            Tree root = new Tree(10);
            root.left = new Tree(20);
            root.right = new Tree(30);
            root.right.left = new Tree(40);
            root.right.right = new Tree(50);

            Console.WriteLine(TreeSize(root));
        }
    }
}
```

