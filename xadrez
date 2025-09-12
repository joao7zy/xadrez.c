#include <stdio.h>
#include <stdlib.h>

//
// FUNÇÕES RECURSIVAS 
//

// Função recursiva para mover o Bispo em uma direção diagonal.
// Parâmetros: linha, coluna atuais; dL e dC indicam a direção do movimento.
void moverBispo(int linha, int coluna, int dL, int dC) {
    // Caso base da recursão: sai da função se sair do tabuleiro (0-7)
    if (linha < 0 || linha >= 8 || coluna < 0 || coluna >= 8) return;

    // Exibe a posição atual onde o Bispo pode se mover
    printf("(%d, %d)\n", linha, coluna);

    // Chamada recursiva para a próxima posição na mesma direção
    moverBispo(linha + dL, coluna + dC, dL, dC);
}

// Função recursiva para movimentação diagonal da Rainha.
// É praticamente igual à do bispo, mas separada para fins didáticos.
void moverRainhaDiagonal(int linha, int coluna, int dL, int dC) {
    if (linha < 0 || linha >= 8 || coluna < 0 || coluna >= 8) return;
    printf("(%d, %d)\n", linha, coluna);
    moverRainhaDiagonal(linha + dL, coluna + dC, dL, dC);
}

//
// FUNÇÕES DE MOVIMENTO
//

// Função para calcular e mostrar os movimentos possíveis da Torre.
// A Torre anda apenas em linha reta: horizontal ou vertical.
void movimentosTorre(int linha, int coluna) {
    printf("\nMovimentos possíveis da Torre:\n");

    // Loop para movimentos horizontais (mesma linha, todas as colunas)
    for (int c = 0; c < 8; c++) {
        if (c != coluna) // evita imprimir a posição atual
            printf("(%d, %d)\n", linha, c);
    }

    // Loop para movimentos verticais (mesma coluna, todas as linhas)
    for (int l = 0; l < 8; l++) {
        if (l != linha) // evita imprimir a posição atual
            printf("(%d, %d)\n", l, coluna);
    }
}

// Função para calcular e mostrar os movimentos possíveis do Bispo.
// O Bispo anda apenas nas diagonais, então usamos recursão para ir
// até o final de cada diagonal.
void movimentosBispo(int linha, int coluna) {
    printf("\nMovimentos possíveis do Bispo:\n");

    // Quatro chamadas recursivas, uma para cada diagonal
    moverBispo(linha+1, coluna+1, 1, 1);   // diagonal inferior direita
    moverBispo(linha+1, coluna-1, 1, -1);  // diagonal inferior esquerda
    moverBispo(linha-1, coluna+1, -1, 1);  // diagonal superior direita
    moverBispo(linha-1, coluna-1, -1, -1); // diagonal superior esquerda
}

// Função para calcular e mostrar os movimentos possíveis da Rainha.
// A Rainha anda como Torre + Bispo, então combinamos loops e recursão.
void movimentosRainha(int linha, int coluna) {
    printf("\nMovimentos possíveis da Rainha:\n");

    //  Parte 1: Movimentos de Torre (horizontal e vertical)
    for (int c = 0; c < 8; c++) {
        if (c != coluna) printf("(%d, %d)\n", linha, c);
    }
    for (int l = 0; l < 8; l++) {
        if (l != linha) printf("(%d, %d)\n", l, coluna);
    }

    //  Parte 2: Movimentos de Bispo (diagonais recursivas)
    moverRainhaDiagonal(linha+1, coluna+1, 1, 1);
    moverRainhaDiagonal(linha+1, coluna-1, 1, -1);
    moverRainhaDiagonal(linha-1, coluna+1, -1, 1);
    moverRainhaDiagonal(linha-1, coluna-1, -1, -1);
}

// Função para calcular e mostrar os movimentos possíveis do Cavalo.
// O Cavalo se move em "L": duas casas numa direção e uma em outra.
void movimentosCavalo(int linha, int coluna) {
    printf("\nMovimentos possíveis do Cavalo:\n");

    // Tabela com as 8 combinações possíveis do movimento em L
    int movimentos[8][2] = {
        {2, 1}, {2, -1}, {-2, 1}, {-2, -1},
        {1, 2}, {1, -2}, {-1, 2}, {-1, -2}
    };

    // Loop que verifica cada movimento
    for (int i = 0; i < 8; i++) {
        int nova_linha = linha + movimentos[i][0];
        int nova_coluna = coluna + movimentos[i][1];

        // Verifica se a nova posição está dentro do tabuleiro
        if (nova_linha >= 0 && nova_linha < 8 &&
            nova_coluna >= 0 && nova_coluna < 8) {
            printf("(%d, %d)\n", nova_linha, nova_coluna);
        }
    }
}

//
//  FUNÇÃO PRINCIPAL 
//
int main() {
    int opcao, linha, coluna;

    do {
        // Exibe menu de seleção de peça
        printf("\n SIMULADOR DE MOVIMENTOS DE XADREZ \n");
        printf("Escolha a peça:\n");
        printf("1 - Torre\n");
        printf("2 - Bispo\n");
        printf("3 - Rainha\n");
        printf("4 - Cavalo\n");
        printf("0 - Sair\n");
        printf("Opção: ");
        scanf("%d", &opcao);

        // Executa apenas se o usuário escolher uma peça válida
        if (opcao >= 1 && opcao <= 4) {
            // Solicita posição inicial no tabuleiro
            printf("Digite a linha (0-7): ");
            scanf("%d", &linha);
            printf("Digite a coluna (0-7): ");
            scanf("%d", &coluna);

            // Verifica se a posição está dentro do tabuleiro
            if (linha < 0 || linha > 7 || coluna < 0 || coluna > 7) {
                printf("\nPosição inválida!\n");
                continue; // volta ao menu
            }

            // Chama a função correspondente à peça escolhida
            switch (opcao) {
                case 1: movimentosTorre(linha, coluna); break;
                case 2: movimentosBispo(linha, coluna); break;
                case 3: movimentosRainha(linha, coluna); break;
                case 4: movimentosCavalo(linha, coluna); break;
            }
        }

    } while (opcao != 0); // repete o menu até o usuário escolher sair

    printf("\nPrograma encerrado.\n");
    return 0; // fim da execução
}
