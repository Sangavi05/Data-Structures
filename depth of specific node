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

int findDepth(TreeNode* root, int value, int currentDepth) {
    if (root == NULL) {
        return -1; // Node not found
    }

    if (root->value == value) {
        return currentDepth; // Node found, return current depth
    }

    int leftDepth = findDepth(root->left, value, currentDepth + 1);
    if (leftDepth != -1) {
        return leftDepth; // Node found in the left subtree
    }

    return findDepth(root->right, value, currentDepth + 1); // Search in the right subtree
}

int main() {
    TreeNode* root = NULL;
    int values[] = {1, 2, 3, 4, 5, 6, 7};
    int n = sizeof(values) / sizeof(values[0]);

    for (int i = 0; i < n; i++) {
        root = insert(root, values[i]);
    }

    int searchValue = 5;
    int depth = findDepth(root, searchValue, 0);

    if (depth != -1) {
        printf("The depth of node with value %d is %d.\n", searchValue, depth);
    } else {
        printf("Node with value %d not found in the binary tree.\n", searchValue);
    }

    return 0;
}
