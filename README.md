#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>

#define MAX 20

void NacitajMaticu(int r, int s, int A[MAX][MAX]) {
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < s; j++) {
            scanf("%d", &A[i][j]);
        }
    }
}

void VypisMaticu(int r, int s, int A[MAX][MAX]) {
    for (int i = 0; i < r; i++) {
        for (int j = 0; j < s; j++) {
            printf("%d ", A[i][j]);
        }
        printf("\n");
    }
}

double AritmPriemerPrvkovNaDiagonale(int r, int s, int A[MAX][MAX]) {
    int sum = 0, count = 0;
    for (int i = 0; i < r && i < s; i++) {
        sum += A[i][i];
        count++;
    }
    return count > 0 ? (double)sum / count : 0.0;
}

int main() {
    int r, s;
    int A[MAX][MAX], B[MAX][MAX];
    
    printf("Zadajte rozmery matíc (r s): ");
    scanf("%d %d", &r, &s);
    
    if (r >= 20 || s >= 20) {
        printf("Rozmery matíc musia byť menšie ako 20.\n");
        return 1;
    }
    
    printf("Zadajte prvky matice A:\n");
    NacitajMaticu(r, s, A);
    
    printf("Zadajte prvky matice B:\n");
    NacitajMaticu(r, s, B);
    
    printf("Matica A:\n");
    VypisMaticu(r, s, A);
    
    printf("Matica B:\n");
    VypisMaticu(r, s, B);
    
    double priemerA = AritmPriemerPrvkovNaDiagonale(r, s, A);
    double priemerB = AritmPriemerPrvkovNaDiagonale(r, s, B);
    
    printf("Aritmeticky priemer prvkov na hlavnej diagonale matice A je: %.2f\n", priemerA);
    printf("Aritmeticky priemer prvkov na hlavnej diagonale matice B je: %.2f\n", priemerB);
    
    return 0;
}
