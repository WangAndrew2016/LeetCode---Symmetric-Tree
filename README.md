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
        vector<int>left;
        vector<int>right;
        buildLeft(root, left);
        buildRight(root, right);
        
        if(left == right)
            return true;
        else
            return false;
        
    }
    
    void buildLeft(TreeNode* root, vector<int>&left)
    {
        if(root!=NULL)
        {
            buildLeft(root->left, left);
            left.push_back(root->val);
            buildLeft(root->right, left);
        }
        
        return;
    }
    
    void buildRight(TreeNode* root, vector<int>&right)
    {
        if(root!=NULL)
        {
            buildRight(root->right, right);
            right.push_back(root->val);
            buildRight(root->left, right);
        }
        
        return;
    }
};
