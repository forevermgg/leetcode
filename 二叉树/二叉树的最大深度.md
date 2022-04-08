```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (root == nullptr) {
            return 0;
        }
        // 层序遍历
        int result = 0;
        queue<TreeNode*> current;
        current.push(root);

        while(!current.empty()) {
            int size  = current.size();
            while(size> 0) {
                TreeNode* node  = current.front();
                current.pop();
                if (node->left) {
                    current.push(node->left);
                }
                if (node->right) {
                    current.push(node->right);
                }
                size = size -1;
            }
            result = result + 1;
        }
        return result;
    }
};
```
