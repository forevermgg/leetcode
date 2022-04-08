```
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
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> result;
        if (root == nullptr) {
           return result;
        }
        
        queue<TreeNode*> que;
        que.push(root);

        while(!que.empty()) {
            int size = que.size();
            vector<int> sub;
            while(size>0) {
                TreeNode* node = que.front();
                que.pop();
                sub.push_back(node->val);
                if(node->left) {
                    que.push(node->left);
                }
                if(node->right) {
                    que.push(node->right);
                }
                size --;
            }
            result.push_back(sub);
        }

        return result;
    }
};
```
