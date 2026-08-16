# Registradores (Registers)


## O que são registradores

Registradores da CPU são locais de armazenamento **pequenos e de alta velocidade** localizados dentro da CPU. São usados para segurar temporariamente dados que estão sendo processados ou manipulados.

- A arquitetura da CPU (32-bit ou 64-bit) refere-se à **largura/tamanho** dos registradores
- Cada CPU tem seu conjunto fixo de registradores
- Pense em registradores como **variáveis temporárias** usadas pela CPU para buscar e armazenar dados

Este curso foca em um grupo específico: os **General Purpose Registers (GPRs)**.



## General Purpose Registers (GPRs)

São usados para armazenar dados temporariamente durante a execução. São versáteis e podem guardar vários tipos de dados: inteiros, endereços de memória ou resultados intermediários de operações.

### Os 8 registradores de propósito geral (x86 / 32-bit)

| Nome x86 | Nome | Propósito |
|----------|------|-----------|
| **EAX** | Accumulator | Usado em operações aritméticas |
| **ECX** | Counter | Usado em instruções de shift/rotate e loops |
| **EDX** | Data | Usado em operações aritméticas e I/O |
| **EBX** | Base | Usado como ponteiro para dados |
| **ESP** | Stack Pointer | Ponteiro para o topo da stack |
| **EBP** | Base Pointer | Ponteiro para a base da stack (frame pointer) |
| **ESI** | Source Index | Ponteiro para a origem em operações de stream |
| **EDI** | Destination Index | Ponteiro para o destino em operações de stream |



## Detalhamento dos registradores

### EAX (Accumulator)
Registrador acumulador primário para operações aritméticas e lógicas. Frequentemente usado para armazenar operandos e receber resultados de cálculos. Em certos contextos, guarda **valores de retorno de funções** e serve como scratch register.

### EBX (Base)
Tipicamente usado como ponteiro para dados na memória ou como endereço-base para operações de memória. Também pode servir como registrador de propósito geral.

### ECX (Counter)
Comumente usado para **controle de loop** e contagem de iterações. Frequentemente usado com a instrução LOOP para implementar loops e tarefas repetitivas.

### EDX (Data)
Usado em conjunto com EAX para certas operações aritméticas que exigem maior faixa de armazenamento (ex: multiplicação e divisão de 64 bits). Também serve como registrador de propósito geral.

### ESI (Source Index)
Comumente usado em operações de manipulação de strings. Guarda o endereço inicial da **origem** (source) durante operações como cópia, comparação ou busca de strings.

### EDI (Destination Index)
Complementa o ESI em manipulação de strings. Guarda o endereço inicial do **destino** (destination) durante operações como cópia ou concatenação.

### ESP (Stack Pointer)
Aponta para o **topo da stack** na memória. Usado para gerenciar a stack, área especial de memória para parâmetros de função, variáveis locais, endereços de retorno e outros dados.

### EBP (Base Pointer)
Usado em conjunto com o ESP para acessar parâmetros e variáveis locais dentro de chamadas de função. Serve como **ponto de referência** para acessar dados armazenados na stack.



## Convenção de nomes por arquitetura

A convenção de nomes evoluiu com o tamanho dos registradores:

- CPUs antigas de 8-bit tinham registradores de 16-bit divididos em duas partes: um **low byte** (sufixo `L`) e um **high byte** (sufixo `H`)
- Na convenção de **16-bit**, combina-se L e H substituindo por `X` (ex: `AX`). Para Stack/Base/Source/Destination Pointer, apenas remove o `L`
- Na representação **32-bit**, o nome é prefixado com `E` (de *extended*) > `EAX`
- Na representação **64-bit**, o `E` é substituído por `R` > `RAX`

### Tabela de nomes por tamanho

| Registrador | Accumulator | Counter | Data | Base |
|-------------|-------------|---------|------|------|
| **64-bit** | RAX | RCX | RDX | RBX |
| **32-bit** | EAX | ECX | EDX | EBX |
| **16-bit** | AX | CX | DX | BX |
| **8-bit** | AH/AL | CH/CL | DH/DL | BH/BL |

| Registrador | Stack Pointer | Base Pointer | Source | Destination |
|-------------|---------------|--------------|--------|-------------|
| **64-bit** | RSP | RBP | RSI | RDI |
| **32-bit** | ESP | EBP | ESI | EDI |
| **16-bit** | SP | BP | SI | DI |
| **8-bit** | SPL | BPL | SIL | DIL |



## Instruction Pointer (EIP)

Além dos 8 GPRs, há outro registrador crucial: o **EIP** (convenção x86).

O Instruction Pointer (EIP) controla a execução do programa armazenando um **ponteiro para o endereço da próxima instrução** (machine code) que será executada.

> **NOTA:** O EIP diz à CPU onde está a próxima instrução.

Este registrador é **central em exploração** (buffer overflows), pois controlar o EIP significa controlar o fluxo de execução do programa.

