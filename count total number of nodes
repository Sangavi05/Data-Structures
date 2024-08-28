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

int countNodes(TreeNode* root) {
    if (root == NULL) {
        return 0;
    }

    return 1 + countNodes(root->left) + countNodes(root->right);
}

int main() {
    TreeNode* root = NULL;
    int values[] = {1, 2, 3, 4, 5, 6, 7};
    int n = sizeof(values) / sizeof(values[0]);

    for (int i = 0; i < n; i++) {
        root = insert(root, values[i]);
    }

    int totalNodes = countNodes(root);
    printf("Total number of nodes in the binary tree: %d\n", totalNodes);

    return 0;
}
