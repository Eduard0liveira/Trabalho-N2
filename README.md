# Trabalho-N2

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define PRODUTOS 200
#define CLIENTES 50

// Gera número aleatório de 0 a n-1
int random(int n) {
    return rand() % n;
}

int main(int argc, char *argv[]) {
    int i, p, npro, ncli;
    int compra[CLIENTES];
    float preco[PRODUTOS];
    float total = 0.0;

    // Iniciar o gerador de números aleatórios
    srand((unsigned)time(NULL));

    // Definir número de produtos (1 a 200)
    npro = random(PRODUTOS) + 1;

    // Gerar preços dos produtos (R$5 a R$100)
    for (i = 0; i < npro; i++) {
        p = 5 + random(96); // 96 = 100 - 5 + 1
        preco[i] = p;
    }

    // Definir número de clientes (1 a 50)
    ncli = random(CLIENTES) + 1;

    // Cada cliente compra 1 produto aleatório
    for (i = 0; i < ncli; i++) {
        compra[i] = random(npro);
        total += preco[compra[i]];
    }

    // Impressão formatada
    printf("===============================================\n");
    printf("            SIMULACAO DE VENDAS DA LOJA        \n");
    printf("===============================================\n\n");

    printf("Total de produtos disponíveis : %d\n\n", npro);
    printf("----------- LISTA DE PRODUTOS -----------\n");
    printf("| Código |    Preço (R$)    |\n");
    printf("------------------------------------------\n");
    for (i = 0; i < npro; i++) {
        printf("| %6d |     %8.2f     |\n", i, preco[i]);
    }
    printf("------------------------------------------\n\n");

    printf("Total de clientes atendidos : %d\n\n", ncli);
    printf("------ LISTA DE COMPRAS DOS CLIENTES ------\n");
    printf("| Cliente | Produto Comprado | Valor (R$) |\n");
    printf("-------------------------------------------\n");
    for (i = 0; i < ncli; i++) {
        printf("| %7d | %16d | %9.2f |\n", i, compra[i], preco[compra[i]]);
    }
    printf("-------------------------------------------\n");
    printf("TOTAL ARRECADADO NO DIA: R$ %.2f\n", total);
    printf("===========================================\n");

    return 0;
}
