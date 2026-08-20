# Introdução ao Assembly



## O que é Assembly Language

Assembly é uma linguagem de programação de **baixo nível** intimamente relacionada às instruções de machine code de uma arquitetura de CPU específica.

- Fornece uma representação **simbólica** das instruções de máquina
- Permite escrever instruções usando **mnemônicos** e labels simbólicos ao invés de código binário
- Arquiteturas diferentes têm seus próprios instruction sets e linguagens assembly

| Arquitetura | Assembly |
|-------------|----------|
| Intel e AMD | x86 assembly |
| ARM | ARM assembly |



## Assembly vs Machine Language

```
Assembly Language          >  Machine Language
mov eax, ebx                  01011010 01011110
add eax, ebx                  10101010 10101010

        Tradução via Assembler + Linker
```

O assembly é a camada legível; o machine language é o que a CPU realmente executa. A correspondência entre eles é praticamente um-para-um.



## Linguagens Assembly específicas de CPU

### Intel Assembly Language (x86/x64)

Específica das arquiteturas x86 e x64 da Intel, amplamente usadas em computadores pessoais, servidores e outros dispositivos de computação.

### ARM Assembly Language

Específica da arquitetura ARM, amplamente usada em dispositivos móveis, sistemas embarcados e, cada vez mais, em outros dispositivos.



## Nomenclatura do Intel Assembly

O assembly da arquitetura Intel é normalmente chamado de:

- **"Intel Assembly Language"** ou **"x86 Assembly Language"** - para a versão 32-bit
- **"x86-64 Assembly Language"** - para a versão 64-bit

Também pode ser referido como:
- **IA-32 Assembly Language** - versão 32-bit (IA = "Intel Architecture")
- **IA-32e** ou **Intel 64** - versão 64-bit

