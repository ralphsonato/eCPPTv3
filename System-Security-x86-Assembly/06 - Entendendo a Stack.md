# Entendendo a Stack


## O que é a Stack

A stack (pilha) é uma estrutura de dados fundamental na ciência da computação e tem papel crucial na execução de programas.

No contexto de gerenciamento de memória de processo, a stack é uma região de memória alocada para armazenar, durante a execução:

- Stack frames (call frames)
- Variáveis locais
- Parâmetros de função
- Endereços de retorno (return addresses)



## Princípio LIFO (Last-In-First-Out)

A stack segue o princípio **LIFO** o último item colocado (push) na stack é o primeiro a ser retirado (pop).

Isso torna a stack ideal para:
- Gerenciar chamadas de função
- Armazenar dados temporários que precisam ser acessados na ordem inversa da inserção

Pense na stack como um **array** usado para salvar endereços de retorno de funções, passar argumentos e armazenar variáveis locais.



## O Stack Pointer (ESP)

A stack é gerenciada por um registrador especial: o **stack pointer** (ESP em x86, RSP em x64).

- O ESP **aponta para o topo da stack**, indicando onde o próximo item será colocado ou retirado
- É modificado a cada operação PUSH ou POP

### Como o ESP se comporta

| Operação | Efeito no ESP |
|----------|---------------|
| **PUSH** (empurrar dado) | ESP é **decrementado** para alocar mais espaço |
| **POP** (retirar dado) | ESP é **incrementado** para recuperar memória |



## Direção de crescimento da Stack

Aqui está um ponto contra-intuitivo importante:

> **A stack NÃO cresce para cima. Ela cresce para BAIXO, em direção aos endereços de memória mais baixos.**

O senso comum sugeriria que a stack cresce para cima (endereços maiores), mas o oposto é verdade.

### Por que a stack cresce para baixo?

Isso se deve a razões **históricas**. Em computadores antigos, a memória era limitada e dividida em duas partes: Heap e Stack. Conhecer os limites da memória permitia ao programador saber o tamanho de cada uma.

Foi decidido que:
- O **Heap** começaria dos endereços baixos e cresceria para **cima**
- A **Stack** começaria do fim da memória e cresceria para **baixo**

```
Endereços ALTOS
┌─────────────────┐
│      STACK      │  < início, cresce para baixo
│                 │
│                 │  (espaço livre entre os dois)
│                 │
│      HEAP       │  < início, cresce para cima
└─────────────────┘
Endereços BAIXOS
```



## Por que a Stack é tão importante

Para buffer overflows e exploit development, a stack é a estrutura central. Entender como ela funciona, como cresce e como os dados são organizados nela é o que permite compreender e explorar essas vulnerabilidades.

