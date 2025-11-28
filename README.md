## 4-bit-Adder

### Entradas:

| Sinal | Descrição |
| :--- | :--- |
| **A** | O primeiro número binário de 4 bits a ser somado. |
| **B** | O segundo número binário de 4 bits a ser somado. |
| **Carry In** | O Carry-in inicial, usado para encadear a soma de vários somadores de 4 bits ou para o primeiro estágio. |

### Saídas:

| Sinal | Descrição |
| :--- | :--- |
| **S** | O resultado da soma dos dois números A + B, um número binário de 4 bits. |
| **Carry Out** | O Carry-out final gerado pelo bit mais significativo, indicando um estouro de 4 bits. |

### Explicação:

O 4-bit-Adder é um circuito combinacional digital projetado para executar a adição binária de dois números de 4 bits.

O que faz: Ele calcula a soma A + B + Carry in, onde A e B são vetores de 4 bits, produzindo um resultado de soma de 4 bits e um bit de carry final.

Como ele faz: O circuito é construído pela cascata de quatro Full-Adders.
1.  O bit menos significativo, A_0 e B_0, é somado no primeiro FA, com Cin como seu *carry-in*.
2.  O C_out de cada Full-Adder é conectado como o C_in do Full-Adder subsequente de ordem superior.
3.  O resultado S é formado pelos bits de soma S_3, S_2, S_1, S_0. O C_out do último estágio é o *carry* final do circuito.

### Half-Adder

| Sinal | Entradas | Saídas |
| :--- | :--- | :--- |
| **Entradas** | A, B | - |
| **Saídas** | S, Carry | - |
| **Explicação** | O Half-Adder é o circuito mais simples de adição. Ele soma dois bits de entrada e produz um bit de Soma e um bit de Carry. |

### Full-Adder 

| Sinal | Entradas | Saídas |
| :--- | :--- | :--- |
| **Entradas** | A, B, C_in | - |
| **Saídas** | S, C_out | - |
| **Explicação** | O Full-Adder é capaz de adicionar três bits de entrada: dois bits de dados A e B e um C_in de uma etapa anterior. Ele produz o bit de Soma e um bit de C_out. |

### Half-Subtractor

| Sinal | Entradas | Saídas |
| :--- | :--- | :--- |
| **Entradas** | Minuendo, Subtraendo | - |
| **Saídas** | Diff, Borrow | - |
| **Explicação** | O Half-Subtractor realiza a subtração de dois bits de entrada: Minuendo (M) e Subtraendo (S). Ele produz um bit de Diff (D) e um bit de Borrow. |

### Full-Subtractor

| Sinal | Entradas | Saídas |
| :--- | :--- | :--- |
| **Entradas** | Minunendo, Subtraendo, Borrow in | - |
| **Saídas** | Diff, Borrow out. | - |
| **Explicação** | O Full-Subtractor realiza a subtração de três bits de entrada: Minuendo (M), Subtraendo (S) e um Borrow In de uma etapa anterior. Ele produz um bit de Diferença (D) e um bit de Borrow Out. |

## Unidade Lógica Aritmética (ULA)
### Entradas:

| Sinal | Bits | Descrição |
| :--- | :--- | :--- |
| **A** | 4 bits | Primeiro operando de dados principal. |
| **B** | 4 bits | Segundo operando de dados principal. |
| **B0, B1, B2** | 1 bit cada | Bits de seleção de controle (Opcode) para o **Demux 3-8**. Estes bits determinam a operação. |
| **C_in** | 1 bit | Vai-um de entrada para o 4-Bit-Adder, usado em operações aritméticas. |
| **I_1** | 1 bit | Bit de controle auxiliar, usado para selecionar entre o operando B e $\bar{B}$ (Not B) no Mux 2-1. |

### Saídas:
| Sinal | Bits | Descrição |
| :--- | :--- | :--- |
| **Out** | 4 bits | O Resultado final da operação selecionada. |

### Explicação:
A Unidade Lógica Aritmética é um circuito combinacional de 4 bits projetado para executar diversas operações lógicas e aritméticas nos operandos A e B.

O que faz: A ULA executa funções como Adição, Subtração, AND, OR, e XOR, com base nos bits de controle.

Como ele faz:
1.  Controle de Operação (Opcode): Os bits B0, B1, B2 controlam um Demux 3-8, que ativa um de seus 8 pinos de saída. Esses pinos atuam como sinais de habilitação para as portas de saída.
2.  Operação Aritmética: O 4-Bit Adder está sempre realizando uma soma, mas seu segundo operando é controlado pelo **Mux 2-1**. O Mux 2-1, controlado pelo bit I_1, seleciona entre o operando B original ou o operando Not B.
    * Com I_1 = 0 (selecionando B) e C_in=0, o circuito realiza a adiçã* A + B.
    * Com I_1 = 1 (selecionando B) e C_in=1, o circuito realiza a subtração via complemento de dois A + B + 1).
3.  Operações Lógicas: Portas 4-Bit And, 4-Bit OR, e 4-Bit XOR realizam as operações lógicas bit a bit.
4.  Seleção de Saída: Todas as operações aritméticas e lógicas são realizadas simultaneamente. O resultado final é selecionado por uma estrutura de Multiplexação (MUX) distribuída:
    * As portas 4-Bit AND (portas de habilitação) na saída de cada bloco funcional usam os sinais do Demux 3-8 para permitir que apenas o resultado da operação desejada passe.
    * As portas 4-Bit OR finais combinam todas essas saídas habilitadas para produzir o resultado final de 4 bits na saída Out.
---
