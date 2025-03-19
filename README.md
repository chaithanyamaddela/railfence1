# railfence1
c programming code for railfence for encryption
#include <stdio.h>
#include <string.h>

int main() {
    char text[100];
    int key;

    printf("Enter the text: ");
    scanf("%[^\n]%*c", text); // TAKING INPUT INCLUDING SPACES
    printf("Enter the no of rails: ");
    scanf("%d", &key);

    int len = strlen(text);
    char rail[key][len];

    // INITIALISE A MATRIX TO STORE ELEMENTS
    for (int i = 0; i < key; i++)
        for (int j = 0; j < len; j++)
            rail[i][j] = '\n';

    // LOOP FOR ARRANGING IN ZIG ZAG PATTAERN
    int row = 0, direction = 1;
    for (int i = 0; i < len; i++) {
        rail[row][i] = text[i];

        if (row == 0)
            direction = 1;  //MOVING DOWN
        else if (row == key - 1)
            direction = -1; // MOVING UP

        row += direction;
    }

    // READ ROW WISE FOR ENCRYPTED TEXT
    printf("Encrypted Text: ");
    for (int i = 0; i < key; i++)
        for (int j = 0; j < len; j++)
            if (rail[i][j] != '\n')
                printf("%c", rail[i][j]);
    printf("\n");

    return 0;
}
