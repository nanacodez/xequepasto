#include <stdio.h>
#include <string.h>
#define SIZE 256  // 64 posições * 4 caracteres por posição

    // Converte notação (file 'a'..'h', rank 1..8) para índice no vetor (0..252, step 4)
    int pos(char file, int rank) {
        int fileIndex = file - 'a'; // 0..7
        return (rank - 1) * 32 + fileIndex * 4;
    }

    void exibirTabuleiro(char tabuleiro[]) {
        for (int i = 0; i < SIZE; i += 4) {
            if (i % 32 == 0) printf("\n");
            printf("%s ", &tabuleiro[i]);
        }
        printf("\n\n");
    }

    // Move preservando o rótulo original da peça (copia etiqueta para destino e marca origem com "...")
    void moverPecaPreservandoRotulo(char tabuleiro[], int origem, int destino) {
        // copia o rótulo (3 chars) da origem para o destino
        snprintf(&tabuleiro[destino], 4, "%s", &tabuleiro[origem]);
        // marca origem
        snprintf(&tabuleiro[origem], 4, "...");
    }

    int main() {
        char tabuleiro[SIZE];
        // Inicializar tabuleiro com ".x."
        for (int i = 0; i < SIZE; i += 4) {
            snprintf(&tabuleiro[i], 4, ".x.");
    }

    // Posiciona peças brancas (linha 1)
    snprintf(&tabuleiro[0], 4, "BT1");  // a1
    snprintf(&tabuleiro[4], 4, "BC1");  // b1
    snprintf(&tabuleiro[8], 4, "BB1");  // c1
    snprintf(&tabuleiro[12], 4, "BD0"); // d1  (Dama)
    snprintf(&tabuleiro[16], 4, "BR0"); // e1  (Rei)
    snprintf(&tabuleiro[20], 4, "BB2"); // f1  (Bispo)
    snprintf(&tabuleiro[24], 4, "BC2"); // g1
    snprintf(&tabuleiro[28], 4, "BT2"); // h1

    // Peões brancos (linha 2) BP1..BP8
    for (int i = 32; i < 64; i += 4) {
        snprintf(&tabuleiro[i], 4, "BP%d", (i - 32) / 4 + 1);
    }

    // Peças pretas (linha 8)
    snprintf(&tabuleiro[224], 4, "PT1"); // a8
    snprintf(&tabuleiro[228], 4, "PC1"); // b8
    snprintf(&tabuleiro[232], 4, "PB1"); // c8
    snprintf(&tabuleiro[236], 4, "PD0"); // d8 (Dama preta)
    snprintf(&tabuleiro[240], 4, "PR0"); // e8 (Rei preto)
    snprintf(&tabuleiro[244], 4, "PB2"); // f8
    snprintf(&tabuleiro[248], 4, "PC2"); // g8
    snprintf(&tabuleiro[252], 4, "PT2"); // h8

    // Peões pretos (linha 7) PP1..PP8
    for (int i = 192; i < 224; i += 4) {
        snprintf(&tabuleiro[i], 4, "PP%d", (i - 192) / 4 + 1);
    }

    printf("=== Tabuleiro Inicial ===\n");
    exibirTabuleiro(tabuleiro);

    // -------- Jogada 1 --------
    // Brancas: e2 -> e4  (BP5)
    moverPecaPreservandoRotulo(tabuleiro, pos('e',2), pos('e',4));
    printf("=== Jogada 1 - Brancas: e2 -> e4 ===\n");
    exibirTabuleiro(tabuleiro);

    // Pretas: e7 -> e5  (PP5)
    moverPecaPreservandoRotulo(tabuleiro, pos('e',7), pos('e',5));
    printf("=== Jogada 1 - Pretas: e7 -> e5 ===\n");
    exibirTabuleiro(tabuleiro);

    // -------- Jogada 2 --------
    // Brancas: Bispo f1 -> c4  (BB2)
    moverPecaPreservandoRotulo(tabuleiro, pos('f',1), pos('c',4));
    printf("=== Jogada 2 - Brancas: Bispo f1 -> c4 ===\n");
    exibirTabuleiro(tabuleiro);

    // Pretas: Cavalo b8 -> c6  (PC1)
    moverPecaPreservandoRotulo(tabuleiro, pos('b',8), pos('c',6));
    printf("=== Jogada 2 - Pretas: Cavalo b8 -> c6 ===\n");
    exibirTabuleiro(tabuleiro);

    // -------- Jogada 3 --------
    // Brancas: Dama d1 -> h5  (BD0)
    moverPecaPreservandoRotulo(tabuleiro, pos('d',1), pos('h',5));
    printf("=== Jogada 3 - Brancas: Dama d1 -> h5 ===\n");
    exibirTabuleiro(tabuleiro);

    // Pretas: Cavalo g8 -> f6  (PC2)
    moverPecaPreservandoRotulo(tabuleiro, pos('g',8), pos('f',6));
    printf("=== Jogada 3 - Pretas: Cavalo g8 -> f6 ===\n");
    exibirTabuleiro(tabuleiro);

    // -------- Jogada 4 (Xeque-Mate) --------
    // Brancas: Dama h5 -> f7 (captura PP6) => xeque-mate
    moverPecaPreservandoRotulo(tabuleiro, pos('h',5), pos('f',7));
    printf("=== Jogada 4 - Brancas: Dama h5 captura f7 -> Xeque-Mate ===\n");
    exibirTabuleiro(tabuleiro);
    
    return 0;
    }
