# Assemblers & Compilers


## O que é um Assembler

No contexto de programação em assembly, um **assembler** é um tipo de tradutor de linguagem que converte código assembly em **machine code**, diretamente executável pela CPU.

Assembly é uma linguagem de baixo nível que usa instruções mnemônicas para representar instruções de máquina, tornando-a mais fácil de ler e escrever do que o machine code binário puro.



## Tipos de Assemblers

Existem vários assemblers, dependendo da ISA (Instruction Set Architecture) do sistema alvo:

| Assembler | Descrição |
|-----------|-----------|
| **MASM** (Microsoft Macro Assembler) | Assembler x86 que usa sintaxe Intel, para MS-DOS e Windows |
| **GAS** (GNU Assembler) | Usado pelo GNU Project, back-end padrão do GCC |
| **NASM** (Netwide Assembler) | x86, escreve programas 16-bit, 32-bit (IA-32) e 64-bit; um dos mais populares no Linux |
| **FASM** (Flat Assembler) | x86, suporta sintaxe Intel em IA-32 e x86-64 |



## Como os Assemblers funcionam

Quando o código-fonte é montado (assembled), o arquivo resultante é chamado de **object file** (arquivo objeto) uma representação binária do programa.

Embora as instruções assembly e o machine code tenham correspondência **um-para-um** e a tradução seja simples, o assembler realiza operações adicionais:
- Atribui localizações de memória a variáveis e instruções
- Resolve nomes simbólicos (symbolic names)

Depois que o assembler cria o object file, é necessário um **linker** para criar o executável de verdade. O linker pega um ou mais object files e os combina para criar o arquivo executável.

### Fluxo Assembly > Executável

```
Código Assembly (.s)
        │  Assembler
        |
Object File (.o)  ──┐
                    │  Linker
Outros .o / libs ───┤
                    |
            Executável
```



## O que é um Compiler

Um **compiler** (compilador) é uma ferramenta usada para traduzir código-fonte escrito em uma linguagem de **alto nível** para machine code ou código executável.

O compiler é similar ao assembler:
- Converte código de alto nível (como C) em código de baixo nível ou diretamente em um object file
- Uma vez criado o arquivo de saída, o processo anterior (linking) é executado sobre ele
- O resultado final é um arquivo executável

---

## Correlação com High-Level Languages (HLLs)

O caminho completo de um código C até virar um executável:

```
1. hello.c / hello.cpp    (código-fonte C)
        │  C Preprocessor
        
2. hello.i                (código pré-processado)
        │  C Compiler
        
3. hello.s                (código assembly)
        │  Assembler
        
4. hello.o                (object file)
        │  Linker (+ outras libs/módulos)
        
5. hello / hello.exe      (executável)
        │  armazenado no HDD
        
6. Loader
        
7. Process Address Space (RAM) - programa em execução
```

### Resumo das etapas

| Etapa | Ferramenta | Entrada → Saída |
|-------|-----------|-----------------|
| 1 | Preprocessor | `.c` > `.i` |
| 2 | Compiler | `.i` > `.s` |
| 3 | Assembler | `.s` > `.o` |
| 4 | Linker | `.o` + libs > executável |
| 5 | Loader | executável > RAM (processo) |

