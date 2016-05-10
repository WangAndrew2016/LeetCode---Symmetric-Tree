# LeetCode---Symmetric-Tree
Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).

For example, this binary tree is symmetric:

    1
   / \
  2   2
 / \ / \
3  4 4  3
But the following is not:
    1
   / \
  2   2
   \   \
   3    3
   
   
   
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        
        if(root = NULL)
            return true;
        
        TreeNode *revertNode = revertFun(root);
        return compareTree(root, revertNode);
        
    }
    
    TreeNode *revertFun(TreeNode *root)
    {
        if (root == NULL)
            return NULL;
            
        TreeNode *tmp = revertFun(root->left);
        root->left = revertFun(root->right);
        root->right = tmp;
        
        return root;
    }
    
    bool compareTree(TreeNode* node, TreeNode* revertNode)
    {
        if(node == NULL && revertNode == NULL)
            return true;
        else if(node != NULL && revertNode == NULL)
            return false;
        else if(node == NULL && revertNode != NULL)
            return false;
            
        if(node->val == revertNode->val && compareTree(node->left, revertNode->left) && compareTree(node->right, revertNode->right))
            return true;
        else
            return false;
    }
};
