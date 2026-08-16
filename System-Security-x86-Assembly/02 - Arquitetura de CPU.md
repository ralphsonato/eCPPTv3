# Arquitetura de CPU



## O que é a CPU

A CPU (Central Processing Unit) é frequentemente chamada de "cérebro" do computador, responsável por **executar instruções e realizar cálculos**. É o dispositivo encarregado de executar o **machine code** (código de máquina) de um programa.

O machine code, ou linguagem de máquina, é o conjunto de instruções que a CPU processa.

---

## Instruções

Cada instrução é um **comando primitivo** que realiza uma operação específica, como:

- Mover dados entre registradores
- Trabalhar com memória
- Mudar o fluxo de execução de um programa
- Realizar operações aritméticas

Como regra, cada CPU tem sua própria **Instruction Set Architecture (ISA)**.

---

## Do Machine Code ao Assembly

As instruções da CPU são representadas em formato **hexadecimal (HEX)**. Devido à natureza ilegível e complexa, é impossível para humanos ler ou usar esse formato diretamente.

Por isso, o machine code é traduzido para **Assembly Language (ASM)**:

- Assembly é um código **mnemônico** (linguagem mais legível) que humanos conseguem entender e interpretar
- É uma linguagem de **baixo nível** intimamente relacionada às instruções de machine code de uma arquitetura de CPU específica
- Fornece uma **representação simbólica** das instruções de máquina, permitindo escrever com mnemônicos e labels simbólicos ao invés de código binário

---

## Assembly é específico da arquitetura

O assembly está intimamente ligado à arquitetura da CPU alvo. **Arquiteturas diferentes têm seus próprios instruction sets e linguagens assembly.**

| Arquitetura | Uso |
|-------------|-----|
| **x86 assembly** | Processadores Intel e AMD |
| **ARM assembly** | Processadores baseados em ARM (mobile, embedded) |

---

## Cadeia de tradução

```
Machine Code (HEX)  <->  Assembly (mnemônicos legíveis)
  ilegível p/                    legível p/
   humanos                        humanos
```

