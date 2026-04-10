#include <stdio.h>
#include <stdlib.h>


struct node {
    int data;
    struct node *next;
};

struct node *head = NULL;


void createez8();
void insertz8();
void deleteez8();
void traversez8();

/* Main Function */
int main() {
    int choice;
    
    while (1) {
        printf("\n--- Singly Linked List Menu ---\n");
        printf("1. Create\n");
        printf("2. Insert5AA\n");
        printf("3. Delete\n");
        printf("4. Traverse\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        
        switch (choice) {
            case 1: createz8();
                    break;
            case 2: insertz8();
                    break;
            case 3: deleteez8();
                    break;
            case 4: traversez8();
                    break;
            case 5: exit(0);
            default: printf("Invalid choice\n");
        }
    }
    return 0;
}

/* Create Linked List */
void createz8() {
    int n, i, value;
    struct node *temp, *newnode;
    
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    
    for (i = 0; i < n; i++) {
        newnode = (struct node *)malloc(sizeof(struct node));
        printf("Enter data: ");
        scanf("%d", &value);
        
        newnode->data = value;
        newnode->next = NULL;
        
        if (head == NULL) {
            head = newnode;
        } else {
            temp = head;
            while (temp->next != NULL)
                temp = temp->next;
            temp->next = newnode;
        }
    }
}

/* Insert at End */
void insertz8() {
    int value;
    struct node *newnode, *temp;
    
    newnode = (struct node *)malloc(sizeof(struct node));
    printf("Enter value to insert: ");
    scanf("%d", &value);
    
    newnode->data = value;
    newnode->next = NULL;
    
    if (head == NULL) {
        head = newnode;
    } else {
        temp = head;
        while (temp->next != NULL)
            temp = temp->next;
        temp->next = newnode;
    }
}

/* Delete a Node */
void deleteez8() {
    int value;
    struct node *temp, *prev;
    
    if (head == NULL) {
        printf("List is empty\n");
        return;
    }
    
    printf("Enter value to delete: ");
    scanf("%d", &value);
    
    temp = head;
    
    if (temp->data == value) {
        head = temp->next;
        free(temp);
        printf("Node deleted\n");
        return;
    }
    
    while (temp != NULL && temp->data != value) {
        prev = temp;
        temp = temp->next;
    }
    
    if (temp == NULL) {
        printf("Value not found\n");
    } else {
        prev->next = temp->next;
        free(temp);
        printf("Node deleted\n");
    }
}
/* Traverse the List */
void traversez8() {
    struct node *temp;
    
    if (head == NULL) {
        printf("List is empty\n");
        return;
    }
    
    temp = head;
    printf("Linked List: ");
    while (temp != NULL) {
        printf("%d -> ", temp->data);
        temp = temp->next;
    }
    printf("NULL\n");}
