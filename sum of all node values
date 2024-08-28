#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;            
    struct Node *left;   
    struct Node *right;  
} Node;

Node* createNode(int data) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

int sumOfNodes(Node* root) {
    if (root == NULL) {
        return 0;
    }

    int leftSum = sumOfNodes(root->left);
    int rightSum = sumOfNodes(root->right);
    return root->data + leftSum + rightSum;
}

void insertNode(Node** root, int data) {
    if (*root == NULL) {
        *root = createNode(data);
        return;
    }

    Node* queue[100];
    int front = 0;
    int rear = 0;

    queue[rear++] = *root;

    while (front < rear) {
        Node* current = queue[front++];

        if (current->left == NULL) {
            current->left = createNode(data);
            return;
        } else {
            queue[rear++] = current->left;
        }

        if (current->right == NULL) {
            current->right = createNode(data);
            return;
        } else {
            queue[rear++] = current->right;
        }
    }
}

void freeTree(Node* root) {
    if (root != NULL) {
        freeTree(root->left);
        freeTree(root->right);
        free(root);
    }
}

int main() {
    Node* root = NULL;

    insertNode(&root, 10);
    insertNode(&root, 5);
    insertNode(&root, 20);
    insertNode(&root, 1);
    insertNode(&root, 15);
    insertNode(&root, 25);
    insertNode(&root, 30);

    int totalSum = sumOfNodes(root);

    printf("Sum of all node values in the binary tree: %d\n", totalSum);

    freeTree(root);

    return 0;
}
