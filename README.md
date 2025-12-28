# Todo-List-using--c
Simple-todo-list in C
#include <stdio.h>
#include <string.h>
struct Todo {
    int id;
    char task[100];
};
int main() {
    struct Todo list[100];
    int choice, count = 0, i, id, found;
    while (1) {
        printf("\n--- TO DO LIST ---\n");
        printf("1. Add Task\n");
        printf("2. View Tasks\n");
        printf("3. Delete Task\n");
        printf("4. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        switch (choice) {
        case 1:
            printf("Enter task: ");
            getchar();  // clear buffer
            fgets(list[count].task, 100, stdin);
            list[count].id = count + 1;
            count++;
            printf("Task added successfully!\n");
            break;
        case 2:
            printf("\nYour Tasks:\n");
            for (i = 0; i < count; i++) {
                printf("%d. %s", list[i].id, list[i].task);
            }
            break;
        case 3:
            printf("Enter task ID to delete: ");
            scanf("%d", &id);
            found = 0;
            for (i = 0; i < count; i++) {
                if (list[i].id == id) {
                    found = 1;
                    for (int j = i; j < count - 1; j++) {
                        list[j] = list[j + 1];
                    }
                    count--;
                    printf("Task deleted!\n");
                    break;
                }
            }
            if (!found)
                printf("Task not found!\n");
            break;
        case 4:
            printf("Exiting...\n");
            return 0;
        default:
            printf("Invalid choice!\n");
        }
    }
}
