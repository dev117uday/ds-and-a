---
description: Linkedlist
---

# C++

### biggest\_element.cpp 

```text
#include <iostream>

using namespace std;

struct Tree {
    Tree* left;
    Tree* right;
    int number;
};

int getSize(Tree *root){
    if (root == nullptr) {
        return 0;
    }
    return 1+getSize(root->right)+getSize(root->left);
}

int bigger_number(int x, int y){
    if (x>y)
        return x;
    return y;
}

int biggest(Tree *root) {
    if (root == nullptr) {
        return INT32_MIN;
    } else {
        return bigger_number(root->number,bigger_number(biggest(root->left),biggest(root->right)));
    }
}

int main(){
    Tree my_tree{};
    cout << "20 10 40 30 50 \n";
    my_tree.number = 10;
    my_tree.left = new Tree{nullptr, nullptr,20};
    my_tree.right = new Tree{nullptr, nullptr,30};
    my_tree.right->left = new Tree{nullptr, nullptr, 40};
    my_tree.right->right = new Tree{nullptr, nullptr,50};
    cout << "Size : " << biggest(&my_tree) << endl;

}
```

### get\_size.cpp

```text
#include <iostream>

using namespace std;

struct Tree {
    Tree* left;
    Tree* right;
    int number;
};

int getSize(Tree *root){
    if (root == nullptr) {
        return 0;
    }
    return 1+getSize(root->right)+getSize(root->left);
}

int main(){
    Tree my_tree{};
    cout << "20 10 40 30 50 \n";
    my_tree.number = 10;
    my_tree.left = new Tree{nullptr, nullptr,20};
    my_tree.right = new Tree{nullptr, nullptr,30};
    my_tree.right->left = new Tree{nullptr, nullptr, 40};
    my_tree.right->right = new Tree{nullptr, nullptr,50};
    cout << "Size : " << getSize(&my_tree) << endl;

}
```

### height\_bst.cpp

```text
#include <iostream>

using namespace std;

struct Tree {
    Tree* left;
    Tree* right;
    int number;
};

int height_bst(Tree *root) {
    if (root == nullptr) {
        return 0;
    } else {
        int lDepth = height_bst(root->left);
        int rDepth = height_bst(root->right);

        if ( lDepth > rDepth) {
            return lDepth+1;
        } else {
            return rDepth+1;
        }
    }
}

int main(){
    Tree my_tree{};
    cout << "20 10 40 30 50 \n";
    my_tree.number = 10;
    my_tree.left = new Tree{nullptr, nullptr,20};
    my_tree.right = new Tree{nullptr, nullptr,30};
    my_tree.right->left = new Tree{nullptr, nullptr, 40};
    my_tree.right->right = new Tree{nullptr, nullptr,50};
    cout << height_bst(&my_tree) << " ";
    cout << "\n";
}
```

### transversal.cpp

```text
#include <iostream>

using namespace std;

struct Tree {
    Tree* left;
    Tree* right;
    int number;
};

void inorder(Tree *root) {
    if (root != nullptr) {
        inorder(root->left);
        cout << root->number << " ";
        inorder(root->right);
    }
}

void preorder(Tree *root) {
    if (root != nullptr) {
        cout << root->number << " ";
        preorder(root->left);
        preorder(root->right);
    }
}

void postorder(Tree *root) {
    if (root != nullptr){
        postorder(root->left);
        preorder(root->right);
        cout << root->number << " ";
    }
}

int main(){
    Tree my_tree{};
    cout << "20 10 40 30 50 \n";
    my_tree.number = 10;
    my_tree.left = new Tree{nullptr, nullptr,20};
    my_tree.right = new Tree{nullptr, nullptr,30};
    my_tree.right->left = new Tree{nullptr, nullptr, 40};
    my_tree.right->right = new Tree{nullptr, nullptr,50};
   inorder(&my_tree);
   cout << "\n";
   preorder(&my_tree);
   cout << "\n";
   postorder(&my_tree);
   cout << "\n";
}
```

