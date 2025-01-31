# [270. Closest Binary Search Tree Value](https://leetcode.com/problems/closest-binary-search-tree-value)

[中文文档](/solution/0200-0299/0270.Closest%20Binary%20Search%20Tree%20Value/README.md)

## Description

<p>Given the <code>root</code> of a binary search tree and a <code>target</code> value, return <em>the value in the BST that is closest to the</em> <code>target</code>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://cdn.jsdelivr.net/gh/doocs/leetcode@main/solution/0200-0299/0270.Closest%20Binary%20Search%20Tree%20Value/images/closest1-1-tree.jpg" style="width: 292px; height: 302px;" />
<pre>
<strong>Input:</strong> root = [4,2,5,1,3], target = 3.714286
<strong>Output:</strong> 4
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> root = [1], target = 4.428571
<strong>Output:</strong> 1
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 10<sup>4</sup>]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 10<sup>9</sup></code></li>
	<li><code>-10<sup>9</sup> &lt;= target &lt;= 10<sup>9</sup></code></li>
</ul>

## Solutions

Binary search.

<!-- tabs:start -->

### **Python3**

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def closestValue(self, root: TreeNode, target: float) -> int:
        res, min_diff = root.val, float('inf')
        while root:
            val = abs(root.val - target)
            if min_diff > val:
                min_diff = val
                res = root.val
            if root.val > target:
                root = root.left
            else:
                root = root.right
        return res
```

### **Java**

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public int closestValue(TreeNode root, double target) {
        int res = root.val;
        double minDiff = Double.MAX_VALUE;
        while (root != null) {
            double val = Math.abs(root.val - target);
            if (minDiff > val) {
                minDiff = val;
                res = root.val;
            }
            if (root.val > target) {
                root = root.left;
            } else {
                root = root.right;
            }
        }
        return res;
    }
}
```

### **JavaScript**

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @param {number} target
 * @return {number}
 */
var closestValue = function (root, target) {
    let res = root.val;
    let minDiff = Math.abs(root.val - target);
    while (root) {
        const val = Math.abs(root.val - target);
        if (minDiff > val) {
            minDiff = val;
            res = root.val;
        }
        if (root.val > target) {
            root = root.left;
        } else {
            root = root.right;
        }
    }
    return res;
};
```

### **C++**

```cpp
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
    int closestValue(TreeNode* root, double target) {
        int res = root->val;
        double minDiff = abs(root->val - target);
        while (root != nullptr) {
            double val = abs(root->val - target);
            if (minDiff > val) {
                minDiff = val;
                res = root->val;
            }
            if (root->val > target) {
                root = root->left;
            } else {
                root = root->right;
            }
        }
        return res;
    }
};
```

### **Go**

```go
import "math"

/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func closestValue(root *TreeNode, target float64) int {
	res := root.Val
	minDiff := math.Abs(float64(root.Val) - float64(target))
	for root != nil {
		val := math.Abs(float64(root.Val) - float64(target))
		if minDiff > val {
			minDiff = val
			res = root.Val
		}
		if float64(root.Val) > target {
			root = root.Left
		} else {
			root = root.Right
		}
	}
	return res
}
```

### **...**

```

```

<!-- tabs:end -->
