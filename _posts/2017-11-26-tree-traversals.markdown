---
layout: default
title:  "Tree Traversals"
date:   2017-11-26 12:50:00
categories: cs
---

### Pre-order Traversal
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

### In-order Traversal
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

If you were to translate the regular logic into code, you'd end up with something like this.
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
This doesn't work. You end up in an infinite loop. When you pop `d`, you read `b` again, which adds `d` back into the stack. This 
will happen forever. This is problematic. How can we fix this?

{% highlight ruby %} 
    a
   / \
  b   c
 / \
d   e
{% endhighlight %}

Let's look at how the in-order recursion works. At a high-level, these are the steps:

{% highlight ruby %} 
inorder:
    recurse left
    process node
    recurse right
{% endhighlight %}
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
