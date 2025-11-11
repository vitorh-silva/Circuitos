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
## Half-Subtractor

### Entradas

| Nome | Bits | Descrição |
| :--- | :--- | :--- |
| **A** | 1 | O Minuendo (o primeiro bit a ser subtraído). |
| **B** | 1 | O Subtraendo (o segundo bit). |

### Saídas

| Nome | Bits | Descrição |
| :--- | :--- | :--- |
| **Diferença (D)** | 1 | O resultado da subtração binária. |
| **Borrow Out** | 1 | O Empréstimo de saída. Indica que um empréstimo foi necessário. |

### Explicação

O circuito realiza a operação aritmética A - B para dois bits de entrada e é construído com portas lógicas básicas.

1.  **Porta XOR (Diferença):** Uma porta XOR é usada para gerar a saída de Diferença.
    
2.  **Portas NOT e AND (Borrow Out):** Uma porta NOT (inversor) é usada na entrada A, e seu resultado é ligado a uma porta AND junto com a entrada B.
## Full-Subtractor

### Entradas

| Nome | Bits | Descrição |
| :--- | :--- | :--- |
| **A** | 1 | O Minuendo, bit a ser subtraído. |
| **B** | 1 | O Subtraendo, bit sendo subtraído. |
| **Bi** | 1 | O Borrow In, Empréstimo de Entrada. |

### Saídas

| Nome | Bits | Descrição | |
| :--- | :--- | :--- | :--- |
| **DIFF** | 1 | O resultado da subtração |
| **Borrow Out** | 1 | Indica se um novo empréstimo foi necessário. |

### Explicação

O Full Subtractor é um circuito que realiza a operação de subtração em três bits (A - B - Bi), permitindo a propagação do Borrow entre posições de bits, essencial para subtrações multi-bit. O circuito é construído usando dois Half Subtractors e uma porta OR.

