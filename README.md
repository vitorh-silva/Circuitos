# Circuitos
## 4-bit-Adder

### Entradas

| Nome | Bits | Descrição |
| :--- | :--- | :--- |
| **A** | 4 | O primeiro número binário de 4 bits. |
| **B** | 4 | O segundo número binário de 4 bits. |
| **Carry In** | 1 | O Carry-In da operação. |

### Saídas

| Nome | Bits | Descrição |
| :--- | :--- | :--- |
| **Soma** | 4 | O resultado da Soma dos números A e B. |
| **Carry Out** | 1 | O Carry-Out indicando um "estouro" quando o resultado excede a capacidade de 4 bits, ou seja, a soma é maior que 15. |

### Explicação

O circuito realiza a operação aritmética A + B + Cin.

1.  **Splitters:** Dois componentes Splitter são usados nas entradas A e B para desmembrar o barramento de 4 bits em quatro linhas de 1 bit.
2.  **Ligação dos Full Adders:** Quatro Full Adders são conectados em série, onde as 4 saídas geradas no splitter de A e B são ligadas ao respectivo input de cada full adder.
3.  **Ligação do Carry:** O primeiro a ser ligado é o Cin no primeiro Full Adder. Na sequência, o Carry Out de cada Full Adder é conectado ao Carry In do Full Adder seguinte até finalizar no Output Carry Out.
4.  **Ligação da Soma:** Um terceiro Splitter é usado na saída para agrupar as quatro saídas individuais de 1 bit de soma de cada Full Adder em um único barramento de 4 bits, gerando o output de soma.
