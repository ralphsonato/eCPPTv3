# IA-32 e Setup do Lab



## Por que IA-32?

Neste curso usamos **IA-32 Assembly no Linux**. As razões dessa escolha:

- Um grande número de processadores/sistemas ainda roda IA-32
- Aprender e entender IA-32 é o **melhor ponto de partida** e fornece uma progressão lógica para IA-64

Ou seja, dominar a versão de 32 bits primeiro facilita o entendimento da versão de 64 bits depois.



## Ambiente de Lab IA-32

Os exercícios e demos de IA-32 são realizados em:

| Item | Configuração |
|------|--------------|
| **SO** | Ubuntu 16.04.7 LTS (32-bit) |
| **Virtualização** | VirtualBox |
| **Download** | https://releases.ubuntu.com/16.04/ |

> A escolha de um Ubuntu 32-bit é proposital: permite trabalhar diretamente com registradores e assembly IA-32 sem as camadas de compatibilidade de um sistema 64-bit.



## Ferramentas necessárias no lab

Para montar e compilar programas em assembly no Linux, tipicamente usamos:

```bash
# NASM - assembler para IA-32
sudo apt-get install nasm

# GCC - compilador C e linker
sudo apt-get install gcc

# Ferramentas de debug (úteis no exploit dev)
sudo apt-get install gdb
```



## Fluxo de compilação de um programa Assembly (NASM)

```bash
# 1. Montar o código assembly em object file (formato ELF 32-bit)
nasm -f elf32 programa.asm -o programa.o

# 2. Linkar o object file para gerar o executável
ld -m elf_i386 programa.o -o programa

# 3. Executar
./programa
```

