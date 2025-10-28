---
layout: default
title:  "Tree Traversals"
date:   2017-11-26 12:50:00
categories: cs
---

### Pre-order Traversal
#### Recursive
```
    void preorder(vector<int> &v, TreeNode *root)
    {
        if (root == NULL)
            return;
        
        v.push_back(root->val);
        preorder(v, root->left);
        preorder(v, root->right);
    }
```
#### Iterative
This is probably the easiest to translate to code. When you visit a node, you process it. Then, since we're using a *stack*, we first
push the right child, and then the left child. This ensure that we traverse the left child before the right one.

```
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> result;
        stack<TreeNode *> s;
        
        if (root == NULL)
            return result;
        
        s.push(root);
        while (!s.empty())
        {
            TreeNode *p = s.top();
            s.pop();
            result.push_back(p->val);
            if (p->right)
            {
                s.push(p->right);
            }
            if (p->left)
            {
                s.push(p->left);
            }
        }
        
        return result;
    }
```

### In-order Traversal
#### Recursive
```
    void inorder(vector<int> &v, TreeNode *root)
    {
        if (root == NULL)
            return;

        inorder(v, root->left);
        v.push_back(root->val);
        inorder(v, root->right);
    }
```
#### Iterative
When I first tried converting the recursion logic into code, I ended up with something like this.
```
        s.push(root);
        while (!s.empty())
        {
            TreeNode *p = s.top();

            if (p->left)
            {
                s.push(p->left);
            }

            s.pop();
            result.push_back(p->val);

            if (p->right)
            {
                s.push(p->right);
            }
        }
```
This doesn't work. You end up in an infinite loop. When we pop `d`, we read `b` again. 'b' has a left child (d), so we add `d` back 
into the stack. And this happens forever. Uh oh. How can we fix this?

{% highlight ruby %} 
    a
   / \
  b   c
 / \
d   e
{% endhighlight %}

Let's look at how the in-order recursion works. At a high-level, this is what the recursion does:
```
inorder:
    recurse left
    process node
    recurse right
```
First we recurse over the left sub-tree. Once we are done, we *process* the current node. Then we move onto the right sub-tree. <br>
Logically, we *visit* a node the first time, then we move onto it's left sub-tree. This is the same as storing it on the stack, so that
we can return to it later. When we do return, we want to *process* it, NOT traverse down it's left sub-tree again. We were just there!
The problem now is how do we let the program know that it's already been down the left sub-tree? One way to do it is using a per node
boolean, to keep track of whether or not we've been down that node's left sub-tree. Using a hashmap for this, we end up with code like 
this:

```
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> result;
        stack<TreeNode *> s;
        unordered_map<TreeNode *, bool> hm;
        
        if (root == NULL)
            return result;
        
        TreeNode *p = root;
        s.push(root);
        while (!s.empty())
        {
            p = s.top();
            if (p->left && !hm[p])
            {
                hm[p] = true;
                s.push(p->left);
            }
            else
            {
                result.push_back(p->val);
                s.pop();
                if (p->right)
                {
                    s.push(p->right);
                }
            }
        }
        
        return result;
    }
```
There is a less intuitive way (at least to me) of doing this using a pointer that tracks the current node. The idea is to have the
pointer keep traversing to the left child. Each node it points to is pushed onto the stack. This will keep happening until it eventually
becomes NULL. When this happens, we pop off the stack and process the popped node. Once done, we change the pointer to point to the 
right child of the popped node. Repeat till the stack is empty. <br>
Why does this work? Because the action of moving the pointer until it hits a NULL is effectively the same as having a boolean that tells
us that the left sub-tree has been traversed. We only pop if there is no left-subtree or we've moved past the *right-most child of the 
left sub-tree*. It's a little tricky, but it works. Here is what the implementation looks like:

```
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> result;
        stack<TreeNode *> s;
        
        if (root == NULL)
            return result;
        
        TreeNode *p = root;
        while (true)
        {
            if (p)
            {
                s.push(p);
                p = p->left;
            }
            else
            {
                if (s.empty())
                {
                    break;
                }
                p = s.top();
                s.pop();
                result.push_back(p->val);
                p = p->right;
            }
        }
        
        return result;
    }
```

### Post-order Traversal
```
    void postorder(vector<int> &v, TreeNode *root)
    {
        if (root == NULL)
            return;
     
        postorder(v, root->left);
        postorder(v, root->right);
        v.push_back(root->val);
    }
```



