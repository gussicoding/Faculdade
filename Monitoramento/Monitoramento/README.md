# Desafio de Monitoramento de Temperatura

## 1. Identificação

- **Nome do aluno:** GUSTAVO HENRIQUE DA SILVA
- **Disciplina:** ALGORITMOS E PENSAMENTO COMPUTACIONAL
- **Professora:** Profa. Karla Sartin
- **Título do projeto:** Desafio de Monitoramento de Temperatura

---

## 2. Objetivo

O objetivo deste projeto é desenvolver, em linguagem C, um programa capaz de monitorar leituras de temperatura a partir de um limite definido pelo usuário.

Durante o monitoramento, o programa verifica se cada temperatura está acima ou dentro do limite, controla a quantidade de temperaturas consecutivas acima desse valor e encerra automaticamente quando encontra três temperaturas consecutivas acima do limite.

Ao final, o programa apresenta um relatório com a quantidade de leituras válidas, quantidade e percentual de temperaturas acima do limite, média, maior e menor temperatura registradas.

---

## 3. Funcionamento do programa

### Definição do limite de temperatura

Antes do início do monitoramento, o programa solicita que o usuário informe um valor numérico para representar o limite de temperatura.

Caso seja digitado um valor que não seja numérico, a entrada é considerada inválida e o programa solicita o limite novamente.

### Realização das leituras

Depois que o limite é definido, o programa começa a solicitar as temperaturas uma por uma.

O valor `999` foi reservado como comando para encerrar o monitoramento manualmente. Esse valor não é contabilizado como uma leitura de temperatura.

### Tratamento de valores inválidos

O programa utiliza o retorno da função `scanf` para verificar se a entrada digitada é realmente numérica.

Quando o usuário digita letras ou outro conteúdo que não pode ser convertido para número, o programa:

1. informa que a entrada é inválida;
2. limpa o conteúdo incorreto do buffer de entrada;
3. solicita um novo valor.

### Identificação de temperaturas acima do limite

Cada temperatura válida é comparada com o limite informado.

Quando a temperatura é maior que o limite:

- a quantidade de temperaturas acima do limite aumenta;
- o contador de temperaturas consecutivas aumenta;
- uma mensagem de alerta é exibida.

Quando a temperatura é menor ou igual ao limite, ela é considerada dentro do limite e o contador de temperaturas consecutivas é reiniciado.

### Contagem de temperaturas consecutivas

A variável `consecutivasAcima` começa com valor zero.

Sempre que uma temperatura fica acima do limite, ela é incrementada em 1.

Se aparecer uma temperatura dentro do limite, a variável volta para zero.

Dessa forma, somente uma sequência realmente consecutiva consegue chegar ao valor 3.

### Condição de encerramento

O monitoramento pode terminar de duas maneiras:

- **automaticamente:** quando são registradas três temperaturas consecutivas acima do limite;
- **manualmente:** quando o usuário digita `999`.

Ao terminar, o programa gera um relatório final.

---

## 4. Estruturas de repetição utilizadas

### `do...while`

O `do...while` foi utilizado na leitura do limite de temperatura.

Essa estrutura é adequada porque o programa precisa solicitar o limite pelo menos uma vez. Depois dessa primeira execução, a condição é testada e, se a entrada for inválida, a pergunta é repetida.

### `while`

O `while` foi utilizado no monitoramento das temperaturas.

Antes de cada nova repetição, o programa verifica se a quantidade de temperaturas consecutivas acima do limite ainda é menor que 3.

Enquanto essa condição for verdadeira, novas leituras podem ser realizadas.

A escolha do `while` facilita representar a ideia de:

> continuar monitorando enquanto ainda não ocorreram três temperaturas consecutivas acima do limite.

---

## 5. Como executar

### Compilação

Em um terminal com o GCC instalado, entre na pasta do projeto e execute:

```bash
gcc monitoramento.c -o monitoramento
```

### Execução no Windows

```bash
monitoramento.exe
```

### Execução no Linux/macOS

```bash
./monitoramento
```

---

## 6. Testes realizados

### Teste 1 — Validação de entradas inválidas

**Objetivo:** verificar se o programa rejeita entradas que não são numéricas.

**Entradas utilizadas:**

- limite: `abc` (inválido)
- limite: `30`
- temperatura: `x` (inválida)
- temperatura: `25`
- encerramento: `999`

**Resultado esperado e obtido:**

O programa rejeitou `abc` e `x`, solicitando novos valores. A temperatura `25` foi registrada normalmente e o monitoramento foi encerrado manualmente com `999`.

**Evidência:** `evidencias/teste01.png`

---

### Teste 2 — Temperaturas acima do limite, porém não consecutivas

**Objetivo:** verificar se o contador de temperaturas consecutivas é reiniciado corretamente.

**Limite utilizado:** `30`

**Temperaturas:**

`31, 29, 32, 28, 33`

Depois das leituras, foi digitado `999` para encerrar manualmente.

**Resultado esperado e obtido:**

As temperaturas `31`, `32` e `33` ficaram acima do limite, porém entre elas apareceram temperaturas dentro do limite. Por isso, o contador foi reiniciado e não ocorreu encerramento automático.

O relatório final registrou:

- 5 leituras válidas;
- 3 temperaturas acima do limite;
- 60% das temperaturas acima do limite;
- média de 30,60 °C;
- maior temperatura de 33 °C;
- menor temperatura de 28 °C.

**Evidência:** `evidencias/teste02.png`

---

### Teste 3 — Três temperaturas consecutivas acima do limite

**Objetivo:** verificar o encerramento automático do monitoramento.

**Limite utilizado:** `30`

**Temperaturas:**

`29, 31, 32, 33`

**Resultado esperado e obtido:**

A temperatura `29` ficou dentro do limite. Depois dela, as temperaturas `31`, `32` e `33` ficaram acima do limite de forma consecutiva.

Ao atingir a terceira temperatura consecutiva acima do limite, o programa encerrou o monitoramento automaticamente.

O relatório final registrou:

- 4 leituras válidas;
- 3 temperaturas acima do limite;
- 75% das temperaturas acima do limite;
- média de 31,25 °C;
- maior temperatura de 33 °C;
- menor temperatura de 29 °C.

**Evidência:** `evidencias/teste03.png`

---

## Questão final de reflexão

**Por que você escolheu `while`, `do...while` ou uma combinação das duas estruturas? Em qual parte do algoritmo a diferença entre testar a condição antes ou depois da execução foi importante para sua solução?**

Foi utilizada uma combinação de `do...while` e `while` porque cada estrutura atende melhor a uma parte diferente do programa. O `do...while` foi usado para solicitar o limite de temperatura, pois essa pergunta precisa acontecer pelo menos uma vez. Como a condição é verificada depois da execução, caso o usuário digite uma entrada inválida, o programa repete a solicitação até receber um valor numérico.

Já o `while` foi utilizado no monitoramento das temperaturas porque, antes de solicitar uma nova leitura, o programa pode verificar se ainda não foram detectadas três temperaturas consecutivas acima do limite. Nesse caso, testar a condição antes da repetição ajuda a representar diretamente a regra de continuar o monitoramento somente enquanto a condição de encerramento automático ainda não foi atingida.

---

## Estrutura do repositório

```text
desafio-monitoramento/
│
├── monitoramento.c
├── README.md
└── evidencias/
    ├── teste01.png
    ├── teste02.png
    └── teste03.png
```
