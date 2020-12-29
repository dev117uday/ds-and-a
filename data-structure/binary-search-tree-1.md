---
description: Java implementation for now
---

# Binary Search Tree

### Search in bst : java

```java
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

	static boolean search(Tree root, int x) {
		if (root == null)
			return false;
		if (root.key == x)
			return true;
		else if (root.key > x) {
			return search(root.left, x);
		} else {
			return search(root.right, x);
		}
	}

	public static void main(String[] args) {
		Tree first = new Tree(10);
		first.left = new Tree(5);
		first.left.left = new Tree(4);
		first.left.right = new Tree(6);
		first.right = new Tree(20);
		first.right.left = new Tree(15);
		first.right.right = new Tree(30);
		first.right.right.left = new Tree(27);
		first.right.right.right = new Tree(33);
		System.out.println(search(first, 6));
	}
}
```

### Insert Binary seach tree : java

```java
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

	public static Tree insert(Tree root, int x) {
		if (root == null)
			return new Tree(x);
		else if (root.key < x)
			root.right = insert(root.right, x);
		else if (root.key > x)
			root.left = insert(root.left, x);
		return root;
	}

	public static void main(String[] args) {
		Tree first = new Tree(10);
		first.left = new Tree(5);
		first.left.left = new Tree(4);
		first.left.right = new Tree(6);
		first.right = new Tree(20);
		first.right.left = new Tree(15);
		first.right.right = new Tree(30);
		first.right.right.left = new Tree(27);
		first.right.right.right = new Tree(33);
		insert(first, 21);
		inorder(first);
	}
}
```

### Delete in BST : java

```java
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

	public static Tree getSuccessor(Tree curr) {
		curr = curr.right;
		while (curr != null && curr.left != null)
			curr = curr.left;
		return curr;
	}

	public static Tree delTree(Tree root, int x) {
		if (root == null)
			return root;
		if (root.key > x)
			root.left = delTree(root.left, x);
		else if (root.key < x)
			root.right = delTree(root.right, x);
		else {
			if (root.left == null) {
				return root.right;
			} else if (root.right == null) {
				return root.left;
			} else {
				Tree succ = getSuccessor(root);
				root.key = succ.key;
				root.right = delTree(root.right, succ.key);
			}
		}
		return root;
	}

	public static void main(String[] args) {
		Tree first = new Tree(10);
		first.left = new Tree(5);
		first.left.left = new Tree(4);
		first.left.right = new Tree(6);
		first.right = new Tree(20);
		first.right.left = new Tree(15);
		first.right.right = new Tree(30);
		first.right.right.left = new Tree(27);
		first.right.right.right = new Tree(33);

		inorder(first);
	}
}
```

### Floor & Ceil in BST : java

```java
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

	public static Tree floor(Tree root, int x) {
		Tree res = null;
		while (root != null) {
			if (root.key == x)
				return root;
			else if (root.key > x)
				root = root.left;
			else {
				res = root;
				root = root.right;
			}
		}
		return res;
	}

	public static Tree ceil(Tree root, int x) {
		Tree res = null;
		while (root != null) {
			if (root.key == x)
				return root;
			else if (root.key < x)
				root = root.right;
			else {
				res = root;
				root = root.left;
			}
		}
		return res;
	}

	public static void main(String[] args) {
		Tree first = new Tree(10);
		first.left = new Tree(5);
		first.left.left = new Tree(4);
		first.left.right = new Tree(6);
		first.right = new Tree(20);
		first.right.left = new Tree(15);
		first.right.right = new Tree(30);
		first.right.right.left = new Tree(27);
		first.right.right.right = new Tree(33);
		System.out.println("Floor: " + (floor(first, 17).key));
		System.out.println("Ceil: " + (ceil(first, 17).key));
	}
}
```





