# Java

#### Level order traversal

```text
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
	int maxwidth(tree root) {
		return 11;
	}

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

#### Max width tree

```text
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

#### binary tree to doubly linkedlist

```text
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

#### Construct tree from inorder 

```text
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



