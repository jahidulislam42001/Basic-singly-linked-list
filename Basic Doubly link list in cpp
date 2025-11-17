#include <stdio.h>
#include <stdlib.h>

struct node
{
    int data;
    struct node *prev;
    struct node *next;
};
struct node *head;

void PrintLinkedList()
{
    printf("Current List : ");
    if (head == NULL)
    {
        printf("The LinkedList Is Empty\n\n");
        return;
    }

    struct node *pointer = head;
    while (pointer != NULL)
    {
        printf("%d ", pointer->data);
        pointer = pointer->next;
    }

    printf("\n\n");
}

int CountNode()
{
    int count = 0;
    struct node *pointer = head;
    while (pointer != NULL)
    {
        count++;
        pointer = pointer->next;
    }
    return count;
}

void insertTail(int data)
{
    struct node *newNode = (struct node *)malloc(sizeof(struct node));
    newNode->data = data;
    newNode->next = NULL;

    if (head == NULL)
    {
        newNode->prev = NULL;
        head = newNode;
        return;
    }

    struct node *pointer = head;
    while (pointer->next != NULL)
    {
        pointer = pointer->next;
    }

    pointer->next = newNode;
    newNode->prev = pointer;
}

void insertHead(int data)
{
    struct node *newNode = (struct node *)malloc(sizeof(struct node));
    newNode->data = data;
    newNode->prev = NULL;
    newNode->next = head;

    if (head != NULL)
    {
        head->prev = newNode;
    }

    head = newNode;
}

void AddAtAnyPos(int data, int pos)
{
    int size = CountNode();
    if (pos < 1 || pos > size + 1)
    {
        printf("Out of range\n");
        return;
    }

    if (pos == 1)
    {
        insertHead(data);
        return;
    }

    struct node *pointer = head;
    int count = 1;
    while (count < pos - 1 && pointer != NULL)
    {
        pointer = pointer->next;
        count++;
    }

    struct node *newNode = (struct node *)malloc(sizeof(struct node));
    newNode->data = data;
    newNode->next = pointer->next;
    newNode->prev = pointer;

    if (pointer->next != NULL)
    {
        pointer->next->prev = newNode;
    }

    pointer->next = newNode;
    printf("After adding node at position '%d'\n", pos);
}

void AddAfterElement(int DataToInsert, int DataToFind)
{
    struct node *pointer = head;

    while (pointer != NULL)
    {
        if (pointer->data == DataToFind)
        {
            struct node *newNode = malloc(sizeof(struct node));

            newNode->data = DataToInsert;
            newNode->next = pointer->next;
            newNode->prev = pointer;

            if (pointer->next != NULL)
            {
                pointer->next->prev = newNode;
            }

            pointer->next = newNode;
            printf("Added %d after %d\n", DataToInsert, DataToFind);
            return;
        }
        pointer = pointer->next;
    }

    printf("%d not found in the list\n", DataToFind);
}

void AddBeforeElement(int DataToInsert, int DataToFind)
{
    struct node *pointer = head;

    while (pointer != NULL)
    {
        if (pointer->data == DataToFind)
        {
            struct node *newNode = (struct node *)malloc(sizeof(struct node));

            newNode->data = DataToInsert;
            newNode->next = pointer;
            newNode->prev = pointer->prev;

            if (pointer->prev == NULL)
            {
                head = newNode;
            }
            else
            {
                pointer->prev->next = newNode;
            }

            pointer->prev = newNode;
            printf("Added %d before %d\n", DataToInsert, DataToFind);
            return;
        }
        pointer = pointer->next;
    }

    printf("%d not found in the list\n", DataToFind);
}

void DeleteFirstNode()
{
    if (head == NULL)
    {
        printf("List is already empty!\n");
        return;
    }

    struct node *temp = head;
    head = head->next;

    if (head != NULL)
    {
        head->prev = NULL;
    }

    free(temp);
}

void DeleteTail()
{
    if (head == NULL)
    {
        printf("The List Is Already empty!\n");
        return;
    }

    if (head->next == NULL)
    {
        free(head);
        head = NULL;
        return;
    }

    struct node *pointer = head;
    while (pointer->next != NULL)
    {
        pointer = pointer->next;
    }

    pointer->prev->next = NULL;
    free(pointer);
}

void DeleteAnyNode(int pos)
{
    int size = CountNode();
    if (pos < 1 || pos > size)
    {
        printf("Out of range\n");
        return;
    }

    if (pos == 1)
    {
        DeleteFirstNode();
        return;
    }

    struct node *pointer = head;
    int count = 1;
    while (count < pos && pointer != NULL)
    {
        pointer = pointer->next;
        count++;
    }

    if (pointer->next != NULL)
    {
        pointer->next->prev = pointer->prev;
    }

    pointer->prev->next = pointer->next;
    free(pointer);
}

void clearList()
{
    while (head != NULL)
    {
        struct node *temp = head;
        head = head->next;
        free(temp);
    }
}

int searchVal(int val)
{
    int pos = 1;
    struct node *pointer = head;

    while (pointer != NULL)
    {
        if (pointer->data == val)
        {
            return pos;
        }
        pos++;
        pointer = pointer->next;
    }

    return -1;
}

void reverseLinkedList()
{
    struct node *current = head;
    struct node *temp = NULL;

    while (current != NULL)
    {
        temp = current->prev;
        current->prev = current->next;
        current->next = temp;
        current = current->prev;
    }

    if (temp != NULL)
    {
        head = temp->prev;
    }

    printf("Reversed List: ");
    PrintLinkedList();
}

void sortLinkedList()
{
    struct node *current = head, *index = NULL;
    int temp;

    if (head == NULL)
    {
        printf("List is empty.\n");
        return;
    }

    while (current != NULL)
    {
        index = current->next;
        while (index != NULL)
        {
            if (current->data > index->data)
            {
                temp = current->data;
                current->data = index->data;
                index->data = temp;
            }
            index = index->next;
        }
        current = current->next;
    }

    printf("List sorted in ascending order.\n");
    PrintLinkedList();
}

void deleteElement(int dataToDelete)
{
    struct node *pointer = head;

    while (pointer != NULL)
    {
        if (pointer->data == dataToDelete)
        {
            if (pointer->prev == NULL)
            {
                head = pointer->next;
                if (head != NULL)
                {
                    head->prev = NULL;
                }
            }
            else
            {
                pointer->prev->next = pointer->next;
                if (pointer->next != NULL)
                {
                    pointer->next->prev = pointer->prev;
                }
            }

            free(pointer);
            printf("Node with data %d deleted.\n", dataToDelete);
            return;
        }
        pointer = pointer->next;
    }

    printf("Node with data %d not found.\n", dataToDelete);
}

int main()
{
    int n, choice, data, position, size, DataToInsert, DataToFind;

    while (1)
    {
        printf("1. Insert at the beginning\n");
        printf("2. Insert in the end\n");
        printf("3. Print the list\n");
        printf("4. Insert at a specific position\n");
        printf("5. Delete a specific node \n");
        printf("6. Delete Head  \n");
        printf("7. Delete Tail \n");
        printf("8. Search a specific value \n");
        printf("9. Insert after any specific element \n");
        printf("10. Insert before any specific element \n");
        printf("11.Clean list \n");
        printf("12.Count Node \n");
        printf("13. Reverse the linkedList \n");
        printf("14. Sort the linked LIst \n");
        printf("15.Delete any element\n");
        printf("0. Exit\n\n");

        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice)
        {
        case 0:
            return 0;
        case 1:
            printf("\nEnter data: ");
            scanf("%d", &n);
            insertHead(n);
            printf("Done\n");
            break;
        case 2:
            printf("\nEnter data: ");
            scanf("%d", &n);
            insertTail(n);
            printf("Done\n\n");
            break;
        case 3:
            PrintLinkedList();
            break;
        case 4:
            printf("\nEnter data(Data and Position): ");
            scanf("%d %d", &data, &position);
            AddAtAnyPos(data, position);
            printf("Done\n\n");
            break;
        case 5:
            printf("\nEnter data: ");
            scanf("%d", &n);
            DeleteAnyNode(n);
            printf("Done\n\n");
            break;
        case 6:
            DeleteFirstNode();
            printf("Done\n\n");
            break;
        case 7:
            DeleteTail();
            printf("Done\n\n");
            break;
        case 8:
            printf("\nEnter data: ");
            scanf("%d", &n);
            int pos = searchVal(n);
            printf("pos : %d\n", pos);
            printf("Done\n\n");
            break;
        case 9:
            printf("\nEnter data(Data to insert and Data to Find): ");
            scanf("%d %d", &DataToInsert, &DataToFind);
            AddAfterElement(DataToInsert, DataToFind);
            printf("Done\n\n");
            break;
        case 10:
            printf("\nEnter data(Data to insert and Data to Find): ");
            scanf("%d %d", &DataToInsert, &DataToFind);
            AddBeforeElement(DataToInsert, DataToFind);
            printf("Done\n\n");
            break;
        case 11:
            clearList();
            printf("Done\n\n");
            break;
        case 12:
            size = CountNode();
            printf("Size of the list is : %d\n", size);
            printf("Done\n\n");
            break;
        case 13:
            reverseLinkedList();
            printf("List reversed.\n");
            break;
        case 14:
            sortLinkedList();
            break;
        case 15:
            printf("\nEnter data to delete: ");
            scanf("%d", &n);
            deleteElement(n);
            printf("Done\n\n");
            break;
        default:
            printf("Wrong input!!!\n");
        }
    }

    return 0;
}
