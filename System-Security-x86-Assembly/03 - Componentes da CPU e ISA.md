# Componentes da CPU e ISA



## Componentes da CPU

### Control Unit (CU)

A Control Unit é responsável por **coordenar e controlar** as operações da CPU. Ela:

- Busca (fetch) instruções da memória
- Decodifica (decode) as instruções
- Gerencia a execução, direcionando o movimento de dados e o fluxo de controle dentro da CPU

### Arithmetic Logic Unit (ALU)

A ALU é o componente responsável por realizar **operações aritméticas e lógicas**:

- Aritméticas: adição, subtração, multiplicação, divisão
- Lógicas: AND, OR, NOT

### Registers (Registradores)

Registradores são locais de armazenamento **pequenos e de alta velocidade** dentro da CPU, usados para guardar dados temporariamente durante o processamento.

| Registrador | Função |
|-------------|--------|
| **Program Counter (PC)** | Guarda o endereço de memória da próxima instrução a ser buscada |
| **Instruction Register (IR)** | Guarda a instrução em execução no momento |
| **Accumulator** | Armazena o resultado de operações aritméticas e lógicas |
| **General-Purpose Registers** | Armazenam valores intermediários e operandos durante a execução |



## Instruction Set Architecture (ISA)

Cada CPU tem sua própria ISA. A ISA é o **conjunto de instruções** que um programador (ou compilador) deve entender e usar para escrever um programa corretamente para aquela CPU e máquina específica.

Em outras palavras, a ISA é **o que o programador consegue enxergar**: memória, registradores, instruções, etc. Ela fornece toda a informação necessária para quem quer escrever um programa naquela linguagem de máquina.



## x86 vs x64

A ISA mais comum é o **x86 instruction set**, que se originou do processador **Intel 8086**.

| Termo | Significado |
|-------|-------------|
| **x86** | Processadores de **32 bits** |
| **x64** (x86_64, AMD64) | Versões de **64 bits** |

