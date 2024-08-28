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


void printInOrder(Node* node) {
    if (node != NULL) {
        printInOrder(node->left);
        printf("%d ", node->data);
        printInOrder(node->right);
    }
}

int main() {
    Node* root = NULL; 

    
    insertNode(&root, 1);
    insertNode(&root, 2);
    insertNode(&root, 3);
    insertNode(&root, 4);
    insertNode(&root, 5);
    insertNode(&root, 6);
    insertNode(&root, 7);

    printf("In-order traversal of the binary tree:\n");
    printInOrder(root);
    printf("\n");

    return 0;
}
