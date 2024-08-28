#include <stdio.h>
#include <stdlib.h>

typedef struct TreeNode {
    int value;
    struct TreeNode *left;
    struct TreeNode *right;
} TreeNode;

TreeNode* createNode(int value) {
    TreeNode* newNode = (TreeNode*)malloc(sizeof(TreeNode));
    newNode->value = value;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

TreeNode* insert(TreeNode* root, int value) {
    if (root == NULL) {
        return createNode(value);
    }

    if (root->left == NULL) {
        root->left = createNode(value);
    } else if (root->right == NULL) {
        root->right = createNode(value);
    } else {
        if (root->left->left == NULL || root->left->right == NULL) {
            root->left = insert(root->left, value);
        } else {
            root->right = insert(root->right, value);
        }
    }
    
    return root;
}

int height(TreeNode* node) {
    if (node == NULL) {
        return 0;
    }

    int leftHeight = height(node->left);
    int rightHeight = height(node->right);

    return (leftHeight > rightHeight ? leftHeight : rightHeight) + 1;
}

int diameterHelper(TreeNode* root, int* diameter) {
    if (root == NULL) {
        return 0;
    }

    int leftHeight = diameterHelper(root->left, diameter);
    int rightHeight = diameterHelper(root->right, diameter);

    int currentDiameter = leftHeight + rightHeight;
    if (currentDiameter > *diameter) {
        *diameter = currentDiameter;
    }

    return (leftHeight > rightHeight ? leftHeight : rightHeight) + 1;
}

int diameter(TreeNode* root) {
    int diameter = 0;
    diameterHelper(root, &diameter);
    return diameter;
}

int main() {
    TreeNode* root = NULL;
    int values[] = {1, 2, 3, 4, 5, 6, 7};
    int n = sizeof(values) / sizeof(values[0]);

    for (int i = 0; i < n; i++) {
        root = insert(root, values[i]);
    }

    int treeDiameter = diameter(root);
    printf("Diameter of the binary tree: %d\n", treeDiameter);

    return 0;
}
