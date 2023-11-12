#include <stdio.h>
#include <string.h>

#define MAX_USERS 10

union UserState
{
    int isActive;
};

struct User
{
    char username[50];
    char password[50];
    union UserState state;
};

struct User users[MAX_USERS];
int userCount = 0;

void registerUser()
{
    if (userCount < MAX_USERS)
    {
        char username[50];
        char password[50];
        int state;

        printf("Enter your username: ");
        fgets(username, sizeof(username), stdin);
        username[strcspn(username, "\n")] = 0; // remove newline character

        printf("Enter your password: ");
        fgets(password, sizeof(password), stdin);
        password[strcspn(password, "\n")] = 0; // remove newline character

        printf("Enter your state [1 or 0] : ");
        scanf("%d", &state);
        getchar(); // consume newline character

        strcpy(users[userCount].username, username);
        strcpy(users[userCount].password, password);
        users[userCount].state.isActive = (state == 1 ? 1 : 0);

        userCount++;
        printf("Registration successful!\n");
    }
    else
    {
        printf("User limit reached. Cannot register more users.\n");
    }
}

int loginUser()
{
    char username[50];
    char password[50];

    printf("Enter your username: ");
    fgets(username, sizeof(username), stdin);
    username[strcspn(username, "\n")] = 0; // remove newline character

    printf("Enter your password: ");
    fgets(password, sizeof(password), stdin);
    password[strcspn(password, "\n")] = 0; // remove newline character

    for (int i = 0; i < userCount; i++)
    {
        if (strcmp(username, users[i].username) == 0 && strcmp(password, users[i].password) == 0 && users[i].state.isActive == 1)
        {
            return i;
        }
    }

    return -1;
}

int main()
{
    int choice;

    do
    {
        printf("1. Register\n2. Login\n3. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        getchar(); // consume newline character

        switch (choice)
        {
        case 1:
            registerUser();
            break;
        case 2:
        {
            int userIndex = loginUser();
            if (userIndex != -1)
            {
                printf("Login successful. Welcome, %s!\n", users[userIndex].username);
            }
            else
            {
                printf("Login failed. Invalid username or password.\n");
            }
        }
        break;
        case 3:
            printf("Goodbye!\n");
            break;
        default:
            printf("Invalid choice. Please try again.\n");
        }
    } while (choice != 3);

    return 0;
}
