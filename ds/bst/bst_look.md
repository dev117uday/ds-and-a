---
description: Linkedlist
---

# Java

## Level order traversal

```java
import java.util.LinkedList;
import java.util.Queue;

class tree {
    int key;
    tree left;
    tree right;

    tree(int key) {
        this.key = key;
        left = null;
        right = null;
    }

}

class Program {

    static void inorderTraversal(tree root) {
        if (root == null) {
            return;
        }
        inorderTraversal(root.left);
        System.out.println(root.key);
        inorderTraversal(root.right);
    }

    static void levelOrder(tree root) {
        if (root == null) {
            return;
        }
        Queue<tree> q = new LinkedList<tree>();
        q.add(root);
        while (!q.isEmpty()) {
            tree node = q.poll();
            System.out.println(node.key);
            if(node.left != null) {
                q.add(node.left);
            }
            if (node.right != null){
                q.add(node.right);
            }

        }
    }

    public static void main(String[] args) {
        tree first = new tree(10);
        first.left = new tree(20);
        first.right = new tree(30);
        first.left.left = new tree(40);
        first.left.right = new tree(50);
        first.right.left = new tree(60);
        first.right.right = new tree(70);
        // inorderTraversal(first);
        levelOrder(first);
    }
}
```

## Max width tree

```java
import java.util.LinkedList;
import java.util.Queue;

class tree {
    int key;
    tree left;
    tree right;

    tree(int key) {
        this.key = key;
        left = null;
        right = null;
    }

}

class Program {
    static int max(int a, int b) {
        if (a > b) {
            return a;
        }
        return b;
    }

    static int maxWidth(tree root) {
        if (root == null) {
            return 0;
        }
        Queue<tree> q = new LinkedList<tree>();
        q.add(root);
        int result = 0;
        while (!q.isEmpty()) {
            int size = q.size();
            tree node = q.poll();
            result = max(result, size);
            if (node.left != null) {
                q.add(node.left);
            }
            if (node.right != null) {
                q.add(node.right);
            }
        }
        return result;
    }

    public static void main(String[] args) {
        tree first = new tree(10);
        first.left = new tree(20);
        first.right = new tree(30);
        first.left.left = new tree(40);
        first.left.right = new tree(50);
        first.right.left = new tree(60);
        first.right.right = new tree(70);
        System.out.println(maxWidth(first));
    }
}
```

## binary tree to doubly linkedlist

```java
class tree {
    int key;
    tree left;
    tree right;

    tree(int key) {
        this.key = key;
        left = null;
        right = null;
    }

}

class Program {
    static tree prev = null;

    static int max(int a, int b) {
        if (a > b) {
            return a;
        }
        return b;
    }

    static void printlinkedlist(tree root) {
        tree temp = root;
        while (temp != null) {
            System.out.println(temp.key);
            temp = temp.right;
        }
    }

    static tree bttodll(tree root) {
        if (root == null) {
            return root;
        }
        tree head = bttodll(root.left);
        if (prev == null) {
            head = root;
        } else {
            root.left = prev;
            prev.right = root;
        }
        prev = root;
        bttodll(root.right);
        return head;
    }

    public static void main(String[] args) {
        tree first = new tree(10);
        first.left = new tree(20);
        first.right = new tree(30);
        first.left.left = new tree(40);
        first.left.right = new tree(50);
        first.right.left = new tree(60);
        first.right.right = new tree(70);
        tree head = bttodll(first);
        printlinkedlist(head);
    }
}
```

## Construct tree from inorder

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node  
{ 
  int key; 
  Node left; 
  Node right; 
  Node(int k){
      key=k;
      left=right=null;
  }
}


class GFG { 

    public static void main(String args[]) 
    { 
        int in[]={20,10,40,30,50};
        int pre[]={10,20,30,40,50};
        int n= in.length;
        Node root=cTree(in, pre, 0, n-1);

        inorder(root);
    }

    static int preIndex=0;
    public static Node cTree(int in[],int pre[],int is,int ie){
        if(is>ie)return null;
        Node root=new Node(pre[preIndex++]);

        int inIndex=is;
        for(int i=is;i<=ie;i++){
            if(in[i]==root.key){
                inIndex=i;
                break;
            }
        }
        root.left=cTree(in, pre, is, inIndex-1);
        root.right=cTree(in, pre, inIndex+1, ie);
        return root;
    }

    public static void inorder(Node root){
        if(root!=null){
            inorder(root.left);
            System.out.print(root.key+" ");
            inorder(root.right);    
        }
    } 
}
```

## Spriral Tree

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node  
{ 
  int key; 
  Node left; 
  Node right; 
  Node(int k){
      key=k;
      left=right=null;
  }
}


class GFG { 

    public static void main(String args[]) 
    { 
        Node root=new Node(1);
        root.left=new Node(2);
        root.right=new Node(3);
        root.left.left=new Node(4);
        root.left.right=new Node(5);
        root.right.left=new Node(6);
        root.right.right=new Node(7);

        printSpiral(root);
    } 

    public static void printSpiral(Node root){
        if (root == null) 
            return; 
        Stack<Node> s1 = new Stack<Node>();  
        Stack<Node> s2 = new Stack<Node>();  

        s1.add(root); 

        while (!s1.isEmpty() || !s2.isEmpty()) { 
            while (!s1.empty()) { 
                Node temp = s1.peek(); 
                s1.pop(); 
                System.out.print(temp.key + " "); 

                if (temp.right != null) 
                    s2.add(temp.right); 

                if (temp.left != null) 
                    s2.add(temp.left); 
            } 

            while (!s2.empty()) { 
                Node temp = s2.peek(); 
                s2.pop(); 
                System.out.print(temp.key + " "); 

                if (temp.left != null) 
                    s1.add(temp.left); 
                if (temp.right != null) 
                    s1.add(temp.right); 
            } 
        }
    }   
}
```

## Diameter of binary tree of max distance from two nodes

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node  
{ 
  int key; 
  Node left; 
  Node right; 
  Node(int k){
      key=k;
      left=right=null;
  }
}


class GFG { 

    public static void main(String args[]) 
    { 
        Node root=new Node(10);
        root.left=new Node(20);
        root.right=new Node(30);
        root.right.left=new Node(40);
        root.right.right=new Node(60);
        root.right.left.left=new Node(50);
        root.right.right.right=new Node(70);

        System.out.println("Height: "+height(root));
        System.out.println("Diameter: "+res);
    } 
    static int res=0;
    public static int height(Node root){
        if(root==null)
            return 0;
        int lh=height(root.left);
        int rh=height(root.right);
        res=Math.max(res,1+lh+rh);

        return 1+Math.max(lh,rh);
    }  
}
```

## Lowest Comman Acestor

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node  
{ 
  int key; 
  Node left; 
  Node right; 
  Node(int k){
      key=k;
      left=right=null;
  }
}


class GFG { 

    public static void main(String args[]) 
    { 
        Node root=new Node(10);
        root.left=new Node(20);
        root.right=new Node(30);
        root.right.left=new Node(40);
        root.right.right=new Node(50);
        int n1=20,n2=50;

        Node ans=lca(root,n1,n2);
        System.out.println("LCA: "+ans.key);
    } 

    public static Node lca(Node root, int n1, int n2){
        if(root==null)return null;
        if(root.key==n1||root.key==n2)
            return root;

        Node lca1=lca(root.left,n1,n2);
        Node lca2=lca(root.right,n1,n2);

        if(lca1!=null && lca2!=null)
            return root;
        if(lca1!=null)
            return lca1;
        else
            return lca2;
    }
}
```

## Burn a Binary Tree from a Leaf

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node  
{ 
  int key; 
  Node left; 
  Node right; 
  Node(int k){
      key=k;
      left=right=null;
  }
}

class Distance{
    int val;
    Distance(int d){val=d;}
}

class GFG { 

    public static void main(String args[]) 
    { 
        Node root=new Node(10);
        root.left=new Node(20);
        root.right=new Node(30);
        root.left.left=new Node(40);
        root.left.right=new Node(50);
        root.left.left.left=new Node(60);
        root.left.left.left.left=new Node(70);
        Distance dist=new Distance(-1);int leaf=50;

        burnTime(root,leaf,dist);
        System.out.print(res);
    } 

    static int res=0;

    public static int burnTime(Node root, int leaf, Distance dist){
        if(root==null)return 0;
        if(root.key==leaf){dist.val=0;return 1;}
        Distance ldist=new Distance(-1),rdist=new Distance(-1);
        int lh=burnTime(root.left,leaf,ldist);
        int rh=burnTime(root.right,leaf,rdist);

        if(ldist.val!=-1){
           dist.val=ldist.val+1;
           res=Math.max(res,dist.val+rh);
        }
        else if(rdist.val!=-1){
            dist.val=rdist.val+1;
            res=Math.max(res,dist.val+lh);
        }
        return Math.max(lh,rh)+1;
    }
}
```

## Count nodes in a Complete Binary Tree

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node  
{ 
  int key; 
  Node left; 
  Node right; 
  Node(int k){
      key=k;
      left=right=null;
  }
}


class GFG { 

    public static void main(String args[]) 
    { 
        Node root=new Node(10);
        root.left=new Node(20);
        root.right=new Node(30);
        root.right.left=new Node(40);
        root.right.right=new Node(50);

        System.out.print(countNode(root));
    } 

    public static int countNode(Node root){
        if(root==null)return 0;
        else
            return 1+countNode(root.left)+countNode(root.right);
    } 
}
```

## De-Serialize tree

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node {
    int key;
    Node left;
    Node right;

    Node(int k) {
        key = k;
        left = right = null;
    }
}

class GFG {

    public static void main(String args[]) {
        Node root = new Node(10);
        root.left = new Node(20);

        ArrayList<Integer> arr = new ArrayList<>();
        serialize(root, arr);
        for (int x : arr) {
            System.out.print(x + " ");
        }
        System.out.println();
        ;
        Node root_new = deSerialize(arr);
        inorder(root_new);

    }

    static final int EMPTY = -1;

    public static void serialize(Node root, ArrayList<Integer> arr) {
        if (root == null) {
            arr.add(EMPTY);
            return;
        }
        arr.add(root.key);
        serialize(root.left, arr);
        serialize(root.right, arr);
    }

    static int index = 0;

    public static Node deSerialize(ArrayList<Integer> arr) {
        if (index == arr.size())
            return null;
        int val = arr.get(index);
        index++;
        if (val == EMPTY)
            return null;
        Node root = new Node(val);
        root.left = deSerialize(arr);
        root.right = deSerialize(arr);
        return root;
    }

    public static void inorder(Node root) {
        if (root != null) {
            inorder(root.left);
            System.out.print(root.key + " ");
            inorder(root.right);
        }
    }
}
```

## Serialize binary tree

```java
import java.util.*;
import java.io.*;
import java.lang.*;

class Node {
    int key;
    Node left;
    Node right;

    Node(int k) {
        key = k;
        left = right = null;
    }
}

class GFG {

    public static void main(String args[]) {
        Node root = new Node(10);
        root.left = new Node(20);

        ArrayList<Integer> arr = new ArrayList<>();
        serialize(root, arr);
        for (int x : arr) {
            System.out.print(x + " ");
        }

    }

    static final int EMPTY = -1;

    public static void serialize(Node root, ArrayList<Integer> arr) {
        if (root == null) {
            arr.add(EMPTY);
            return;
        }
        arr.add(root.key);
        serialize(root.left, arr);
        serialize(root.right, arr);
    }
}
```

## Inorder iteratively

```java
import java.util.Stack;

class Tree {
    int key;
    Tree left;
    Tree right;

    Tree(int key) {
        this.key = key;
        left = null;
        right = null;
    }
}

class Program {

    static void iterInorder(Tree root) {

        Stack<Tree> stack = new Stack<Tree>();
        Tree curr = root;
        while (curr != null || stack.isEmpty() == false) {
            while (curr != null) {
                stack.push(curr);
                curr = curr.left;
            }
            curr = stack.pop();
            System.out.println(curr.key);
            curr = curr.right;
        }
    }

    public static void main(String[] args) {
        Tree first = new Tree(10);
        first.left = new Tree(20);
        first.right = new Tree(30);
        first.left.left = new Tree(40);
        first.left.right = new Tree(50);
        first.right.left = new Tree(60);
        first.right.right = new Tree(70);
        iterInorder(first);
    }
}
```

## Preorder iteratively

```java
import java.util.Stack;

class Tree {
    int key;
    Tree left;
    Tree right;

    Tree(int key) {
        this.key = key;
        left = null;
        right = null;
    }
}

class Program {

    static void iterativePreorder(Tree root) {
        if (root == null) {
            return;
        }
        Stack<Tree> TreeStack = new Stack<Tree>();
        TreeStack.push(root);
        while (TreeStack.empty() == false) {
            Tree myTree = TreeStack.peek();
            System.out.print(myTree.key + " ");
            TreeStack.pop();
            if (myTree.right != null) {
                TreeStack.push(myTree.right);
            }
            if (myTree.left != null) {
                TreeStack.push(myTree.left);
            }
        }
    }

    public static void main(String[] args) {
        Tree first = new Tree(10);
        first.left = new Tree(20);
        first.right = new Tree(30);
        first.left.left = new Tree(40);
        first.left.right = new Tree(50);
        first.right.left = new Tree(60);
        first.right.right = new Tree(70);
        iterativePreorder(first);
    }
}
```

