# Stack Frames e Funções



## O que é um Stack Frame

Um stack frame (também chamado de **activation record** ou **call frame**) é uma estrutura de dados usada pela CPU e pelo sistema operacional para gerenciar chamadas de função e o fluxo de execução dentro de um programa.

Cada stack frame contém informações relacionadas a **uma única chamada de função**, incluindo:

- Parâmetros
- Variáveis locais
- Endereço de retorno (return address)
- Outros dados relevantes



## Procedures e Functions

É importante saber que procedures e funções **alteram o fluxo normal** do processo. Quando uma procedure/função termina, ela retorna o controle para a instrução que a chamou.

### Prologue e Epilogue

Funções contêm dois componentes importantes:

| Componente | Função |
|------------|--------|
| **Prologue** | Prepara a stack para ser usada, como colocar um marcador (bookmark) em um livro |
| **Epilogue** | Quando a função termina, restaura a stack para as configurações do prologue |

A Stack consiste em **stack frames lógicos** (áreas/porções da stack), que são:
- **PUSHed** ao chamar uma função
- **POPped** ao retornar um valor



## Como os Stack Frames funcionam

Quando uma sub-rotina (função/procedure) inicia:
1. Um stack frame é criado e atribuído à localização atual do ESP (topo da stack)
2. Isso permite que a sub-rotina opere **independentemente** na sua própria área da stack

Quando a sub-rotina termina, duas coisas acontecem:
1. O programa recebe os parâmetros passados de volta da sub-rotina
2. O **Instruction Pointer (EIP)** é resetado para a localização do momento da chamada inicial

Em outras palavras, o stack frame **mantém o registro de onde cada sub-rotina deve retornar o controle** quando terminar.



## Exemplo com 3 operações principais

Quando uma função é chamada, ocorrem três operações:

1. Os **argumentos** (entre colchetes) precisam ser avaliados
2. O fluxo de controle **salta para o corpo** da função e executa seu código
3. Ao terminar, um **return statement** é encontrado e o programa retorna para a chamada da função (a próxima instrução no código)



## Passo a Passo com código C

Considere um programa C onde `main()` chama `a()`, e `a()` chama `b()`.

### Step 1 - Entrada no main()

O ponto de entrada do programa é o `main()`. O primeiro stack frame a ser colocado (push) na stack é o do `main()`. O stack pointer é ajustado para o topo e um novo frame de `main()` é criado.

```
┌─────────────┐
│  main()     │ < topo
└─────────────┘
```

### Step 2 - main() chama a()

Dentro do `main()`, a primeira instrução é uma chamada à função `a()`. O stack pointer é ajustado e um novo stack frame para `a()` é criado na stack.

```
┌─────────────┐
│    a()      │ < topo
├─────────────┤
│  main()     │
└─────────────┘
```

### Step 3 - a() chama b()

Ao iniciar `a()`, a primeira instrução é uma chamada a `b()`. Novamente o stack pointer é ajustado e um novo frame para `b()` é colocado no topo.

```
┌─────────────┐
│    b()      │ < topo
├─────────────┤
│    a()      │
├─────────────┤
│  main()     │
└─────────────┘
```

### Step 4 - b() retorna

A função `b()` não faz nada e apenas retorna. Ao completar, o stack pointer volta para sua localização anterior, e o programa retorna ao stack frame de `a()`, continuando com a próxima instrução.

```
┌─────────────┐
│    a()      │ < topo (b() foi removido)
├─────────────┤
│  main()     │
└─────────────┘
```

### Step 5 - a() retorna

A próxima instrução executada é o return statement em `a()`. O frame de `a()` é removido (pop), o stack pointer é resetado, e voltamos ao frame de `main()`.

```
┌─────────────┐
│  main()     │ < topo (a() foi removido)
└─────────────┘
```



## Conclusão

Este foi um overview de como os stack frames funcionam. Para **buffer overflows**, é necessário aprofundar em:
- Qual informação é armazenada
- Onde ela é armazenada
- Como os registradores são atualizados

Esse detalhamento é o que conecta este conhecimento à exploração de vulnerabilidades, controlar o **return address** salvo no stack frame é a base de um buffer overflow clássico.

