// Nome completo: Eduardo Minosso
// Trabalho N2 - Simulação de Vendas em uma Loja
// Professor: Alessandro João Brassanini

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_PRODUTOS 200
#define MAX_CLIENTES 50

int main() {
    float produtos[MAX_PRODUTOS];
    int compras[MAX_CLIENTES];
    int totalProdutos, totalClientes;
    float totalVendas = 0.0;

    // Garante aleatoriedade diferente a cada execução
    srand(time(NULL));

    // Gera quantidade aleatória de produtos (entre 1 e 200)
    totalProdutos = rand() % MAX_PRODUTOS + 1;

    // Gera preços entre R$5,00 e R$100,00
    for (int i = 0; i < totalProdutos; i++) {
        produtos[i] = (rand() % 9601 + 500) / 100.0; // De 5.00 até 100.00
    }

    // Gera quantidade aleatória de clientes (entre 1 e 50)
    totalClientes = rand() % MAX_CLIENTES + 1;

    // Cada cliente compra um produto aleatório
    for (int i = 0; i < totalClientes; i++) {
        compras[i] = rand() % totalProdutos;
    }

    // Exibe os preços dos produtos
    printf("Produtos disponíveis:\n");
    for (int i = 0; i < totalProdutos; i++) {
        printf("Produto %d: R$ %.2f\n", i, produtos[i]);
    }

    // Exibe o que cada cliente comprou
    printf("\nCompras dos clientes:\n");
    for (int i = 0; i < totalClientes; i++) {
        int produtoComprado = compras[i];
        float preco = produtos[produtoComprado];
        totalVendas += preco;
        printf("Cliente %d comprou Produto %d por R$ %.2f\n", i, produtoComprado, preco);
    }

    // Total vendido
    printf("\nTotal de vendas do dia: R$ %.2f\n", totalVendas);

    return 0;
}
