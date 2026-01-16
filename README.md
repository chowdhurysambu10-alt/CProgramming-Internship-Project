# CProgramming-Internship-Project



#include <stdio.h>
#include <string.h>

struct Book {
    int id;
    char name[50];
    char author[50];
    int isIssued;
};
struct Book library[100];
int count = 0;
void addBook();
void displayBooks();
void issueBook();
void returnBook();
int main() {
    int choice;
    do {
        printf("\n===== Library Management System =====\n");
        printf("1. Add Book\n");
        printf("2. Display Available Books\n");
        printf("3. Issue Book\n");
        printf("4. Return Book\n");
        printf("5. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                addBook();
                break;
            case 2:
                displayBooks();
                break;
            case 3:
                issueBook();
                break;
            case 4:
                returnBook();
                break;
            case 5:
                printf("Exiting program...\n");
                break;
            default:
                printf("Invalid choice! Try again.\n");
        }
    }while(choice!=5);
    return 0;
}
void addBook() {
    printf("Enter Book ID->");
    scanf("%d",&library[count].id);
    printf("Enter Book Name->");
    scanf("[^\n]",library[count].name);
    printf("Enter Author Name->");
    scanf("[^\n]",library[count].author);
    library[count].isIssued=0;
    count++;
    printf("Book added successfully!\n");
}
void displayBooks(){
    int found=0;

    printf("\nAvailable Books:\n");
    for (inti=0;i<count;i++) {
        if (library[i].isIssued==0) {
            printf("ID: %d | Name: %s | Author: %s\n",
                   library[i].id,
                   library[i].name,
                   library[i].author);
            found=1;
        }
    }
    if(!found){
        printf("No books available.\n");
    }
}

void issueBook() {
    int id,found=0;
    printf("Enter Book ID to issue: ");
    scanf("%d", &id);
    for (inti=0;i<count;i++) {
        if (library[i].id==id&&library[i].isIssued==0) {
            library[i].isIssued=1;
            printf("Book issued successfully!\n");
            found=1;
            break;
        }
    }
    if(!found){
        printf("Book not available or already issued.\n");
    }
}
void returnBook() {
    int id,found=0;
    printf("Enter Book ID to return: ");
    scanf("%d",&id);
    for (inti=0;i<count;i++){
        if(library[i].id==id&&library[i].isIssued==1) {
            library[i].isIssued=0;
            printf("Book returned successfully!\n");
            found=1;
            break;
        }
    }
    if(!found){
        printf("Invalid Book ID or book was not issued.\n");
    }
}
