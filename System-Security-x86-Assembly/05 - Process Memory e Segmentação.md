# Process Memory e Segmentação



## O que é Process Memory

O gerenciamento de memória de processo é um aspecto fundamental dos sistemas operacionais, responsável por organizar e gerenciar os recursos de memória para os programas em execução (processos).

### Virtual Memory

Sistemas operacionais modernos implementam o conceito de **memória virtual**, que:

- Abstrai os recursos de memória física
- Apresenta a cada processo um **espaço de endereços virtual** próprio
- Cada processo percebe sua memória como um **bloco contíguo** de endereços, começando do endereço 0 e indo até o máximo endereçável

Isso significa que cada processo "acha" que tem toda a memória para si, mesmo compartilhando a memória física com outros processos.



## Segmentação de Memória

A memória de processo é tipicamente dividida em segmentos, cada um com um propósito específico:

| Segmento | Propósito |
|----------|-----------|
| **Code (Text)** | Contém o código executável do programa (instruções) |
| **Data** | Armazena dados inicializados (variáveis globais e estáticas) |
| **BSS** | Contém dados não inicializados, zerados durante a execução |
| **Heap** | Memória alocada dinamicamente para estruturas de dados (malloc/free) |
| **Stack** | Armazena stack frames, variáveis locais e parâmetros de função |



## Detalhamento das regiões

### Text (Instruction Segment)
- Fixo pelo programa, contém o código (instruções)
- Marcado como **read-only**, já que o programa não deve se modificar durante a execução

### Data
- Dividido em dados **inicializados** e **não inicializados**
- Dados inicializados incluem variáveis estáticas e globais predefinidas, que podem ser modificadas

### BSS (Block Started by Symbol)
- Contém os dados **não inicializados**
- Inicializa variáveis que são zeradas ou não têm inicialização explícita (ex: `static int t`)

### Heap
- Começa logo após o segmento BSS
- Durante a execução, o programa pode requisitar mais espaço via system calls `brk` e `sbrk` (usadas por `malloc`, `realloc` e `free`)
- A região de dados pode ser estendida dinamicamente

### Stack
- A última região da memória
- **É a estrutura mais importante** para os propósitos deste curso (e para buffer overflows)



## Layout típico da memória de um processo

```
Endereços ALTOS
┌─────────────────┐
│      STACK      │  < cresce para BAIXO
│                 │
│                 │
│                 │
│      HEAP       │  < cresce para CIMA
├─────────────────┤
│      BSS        │  (dados não inicializados)
├─────────────────┤
│      DATA       │  (dados inicializados)
├─────────────────┤
│   TEXT/CODE     │  (read-only)
└─────────────────┘
Endereços BAIXOS
```

Note que **Stack e Heap crescem em direções opostas**: o Heap parte dos endereços baixos crescendo para cima, e a Stack parte dos endereços altos crescendo para baixo.

