# Hello World e Data Types em Assembly



## Contexto

Estes são os módulos práticos finais do curso: escrever um "Hello World" em assembly IA-32 e entender os tipos de dados e variáveis. Reuni aqui a estrutura e os conceitos para servir de referência.



## Estrutura de um programa Assembly (NASM / IA-32)

Um programa assembly típico é dividido em seções:

| Seção | Propósito |
|-------|-----------|
| `.data` | Dados inicializados (variáveis com valor definido) |
| `.bss` | Dados não inicializados (espaço reservado) |
| `.text` | Código do programa (instruções) — contém o `_start` |



## Hello World em Assembly (IA-32 Linux)

```asm
section .data
    msg db "Hello, World!", 0x0A   ; string + newline
    len equ $ - msg                ; tamanho da string

section .text
    global _start

_start:
    ; syscall write (sys_write = 4)
    mov eax, 4          ; número da syscall (write)
    mov ebx, 1          ; file descriptor (1 = stdout)
    mov ecx, msg        ; ponteiro para a mensagem
    mov edx, len        ; tamanho da mensagem
    int 0x80            ; interrupção do kernel

    ; syscall exit (sys_exit = 1)
    mov eax, 1          ; número da syscall (exit)
    mov ebx, 0          ; código de saída (0 = sucesso)
    int 0x80            ; interrupção do kernel
```

### O que acontece

- `mov` copia valores para os registradores
- `int 0x80` é a interrupção que chama o kernel do Linux para executar a syscall
- A syscall `write` (EAX=4) imprime a string no stdout
- A syscall `exit` (EAX=1) encerra o programa



## Data Types & Variables

No assembly IA-32, definimos dados com diretivas que indicam o tamanho:

### Diretivas de dados inicializados (`.data`)

| Diretiva | Significado | Tamanho |
|----------|-------------|---------|
| `db` | Define Byte | 1 byte |
| `dw` | Define Word | 2 bytes |
| `dd` | Define Doubleword | 4 bytes |
| `dq` | Define Quadword | 8 bytes |

### Diretivas de dados não inicializados (`.bss`)

| Diretiva | Significado | Tamanho |
|----------|-------------|---------|
| `resb` | Reserve Byte | 1 byte |
| `resw` | Reserve Word | 2 bytes |
| `resd` | Reserve Doubleword | 4 bytes |
| `resq` | Reserve Quadword | 8 bytes |

### Exemplos

```asm
section .data
    num1    db  10          ; um byte com valor 10
    num2    dw  1000        ; uma word com valor 1000
    valor   dd  100000      ; doubleword
    texto   db  "abc", 0    ; string terminada em null

section .bss
    buffer  resb 64         ; reserva 64 bytes
    contador resd 1         ; reserva 1 doubleword
```



## Instruções básicas de movimentação e aritmética

```asm
mov eax, 5        ; EAX = 5
mov ebx, eax      ; EBX = EAX (copia valor)

add eax, ebx      ; EAX = EAX + EBX
sub eax, 2        ; EAX = EAX - 2
inc eax           ; EAX = EAX + 1
dec eax           ; EAX = EAX - 1

mul ebx           ; multiplicação (usa EAX)
div ebx           ; divisão (usa EAX e EDX)
```



## Conexão com Exploit Development

Entender como escrever, montar e depurar assembly IA-32 é a base para:
- Escrever **shellcode**
- Analisar programas em **engenharia reversa**
- Construir payloads em **buffer overflows**

Com isso, encerra-se a fundação de System Security e abre-se caminho para o curso de Exploit Development.

