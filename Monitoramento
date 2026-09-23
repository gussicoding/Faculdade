#include <stdio.h>

#define ENCERRAR 999.0f

// Limpa os caracteres que ficaram no teclado quando o usuario digita algo invalido.
void limparBuffer(void) {
    int c;

    while ((c = getchar()) != '\n' && c != EOF) {
        // Apenas descarta os caracteres restantes.
    }
}

int main(void) {
    float limite;
    float temperatura;
    float soma = 0.0f;
    float maior = 0.0f;
    float menor = 0.0f;

    int totalLeituras = 0;
    int acimaDoLimite = 0;
    int consecutivasAcima = 0;
    int entradaValida = 0;
    int encerramentoAutomatico = 0;

    printf("=========================================\n");
    printf("   SISTEMA DE MONITORAMENTO DE TEMPERATURA\n");
    printf("=========================================\n\n");

    // O limite precisa ser informado antes do inicio do monitoramento.
    // O do...while foi escolhido porque a pergunta precisa acontecer
    // pelo menos uma vez e sera repetida se a entrada for invalida.
    do {
        printf("Digite o limite de temperatura: ");

        if (scanf("%f", &limite) != 1) {
            printf("Entrada invalida. Digite um valor numerico.\n\n");
            limparBuffer();
            entradaValida = 0;
        } else {
            entradaValida = 1;
        }
    } while (!entradaValida);

    printf("\nMonitoramento iniciado.\n");
    printf("Digite %.0f para encerrar manualmente.\n\n", ENCERRAR);

    // O while mantem o monitoramento ativo enquanto nao ocorrerem
    // tres temperaturas consecutivas acima do limite.
    while (consecutivasAcima < 3) {
        printf("Digite a temperatura atual: ");

        if (scanf("%f", &temperatura) != 1) {
            printf("Entrada invalida. Digite um valor numerico.\n\n");
            limparBuffer();
            continue;
        }

        // 999 funciona como comando de encerramento e nao entra nos calculos.
        if (temperatura == ENCERRAR) {
            printf("\nMonitoramento encerrado manualmente.\n");
            break;
        }

        // Atualiza a quantidade de leituras e a soma usada na media.
        totalLeituras++;
        soma += temperatura;

        // Na primeira leitura, a propria temperatura vira o maior e o menor valor.
        if (totalLeituras == 1) {
            maior = temperatura;
            menor = temperatura;
        } else {
            if (temperatura > maior) {
                maior = temperatura;
            }

            if (temperatura < menor) {
                menor = temperatura;
            }
        }

        // Verifica se a leitura ultrapassou o limite.
        if (temperatura > limite) {
            acimaDoLimite++;
            consecutivasAcima++;

            printf("ALERTA: temperatura acima do limite!\n");
            printf("Consecutivas acima do limite: %d\n\n", consecutivasAcima);
        } else {
            // Se uma leitura nao estiver acima do limite, a sequencia e quebrada.
            consecutivasAcima = 0;

            printf("Temperatura dentro do limite.\n");
            printf("Contagem consecutiva reiniciada.\n\n");
        }
    }

    // Se o while terminou porque o contador chegou a 3, houve encerramento automatico.
    if (consecutivasAcima == 3) {
        encerramentoAutomatico = 1;
        printf("Tres temperaturas consecutivas acima do limite foram detectadas.\n");
        printf("Monitoramento encerrado automaticamente.\n");
    }

    printf("\n============== RELATORIO FINAL ==============\n");

    if (totalLeituras > 0) {
        float media = soma / totalLeituras;
        float percentualAcima = ((float)acimaDoLimite / totalLeituras) * 100.0f;

        printf("Limite definido: %.2f C\n", limite);
        printf("Total de leituras validas: %d\n", totalLeituras);
        printf("Temperaturas acima do limite: %d\n", acimaDoLimite);
        printf("Percentual acima do limite: %.2f%%\n", percentualAcima);
        printf("Media das temperaturas: %.2f C\n", media);
        printf("Maior temperatura: %.2f C\n", maior);
        printf("Menor temperatura: %.2f C\n", menor);

        if (encerramentoAutomatico) {
            printf("Motivo do encerramento: 3 temperaturas consecutivas acima do limite.\n");
        } else {
            printf("Motivo do encerramento: comando manual do usuario.\n");
        }
    } else {
        printf("Nenhuma temperatura valida foi registrada.\n");
    }

    printf("==============================================\n");

    return 0;
}
