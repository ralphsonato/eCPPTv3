# Operações PUSH e POP


## As operações fundamentais da Stack

Como a stack é uma estrutura LIFO, as operações mais fundamentais são o **PUSH** e o **POP**. O ponteiro principal para essas operações é o **ESP**, que contém o endereço de memória do topo da stack e muda a cada operação.



## PUSH

O **PUSH** adiciona um elemento ao topo da stack. Quando você faz push de um item, ele se torna o novo elemento do topo e a stack cresce em tamanho.

### Passos do PUSH

1. **Decrementar o stack pointer:** o ESP é movido para alocar espaço para o novo elemento
2. **Armazenar o elemento:** o novo elemento é gravado no endereço apontado pelo ESP

> **Atenção:** apesar de o slide falar em "incrementar" conceitualmente para "alocar espaço", na prática (stack cresce para baixo) o PUSH **subtrai** do ESP.

### Como o PUSH funciona em detalhe

Uma instrução PUSH:
- **Subtrai 4** (em 32-bit) ou **8** (em 64-bit) do ESP
- Grava o dado no endereço de memória do ESP
- Atualiza o ESP para o novo topo da stack

Como a stack cresce para trás (para baixo), o PUSH subtrai 4 ou 8 para apontar para um endereço mais baixo. Se não subtraísse, o PUSH sobrescreveria a localização atual apontada pelo ESP (o topo) e perderíamos dados.



## POP

O **POP** remove o elemento do topo da stack. Quando você faz pop de um item, ele é removido do topo e a stack encolhe.

### Passos do POP

1. **Acessar o elemento do topo:** o elemento no topo é recuperado
2. **Incrementar o stack pointer:** o ESP é movido para desalocar o espaço antes ocupado

Em termos de programação, o POP lê o valor armazenado no endereço apontado pelo ESP e depois **adiciona 4** (ou 8) ao ESP para apontar para o próximo elemento.



## Exemplo Prático: PUSH

**Valor inicial:** ESP aponta para o endereço `0x0028FF80`

**Processo:** o programa executa `PUSH 1`
- O ESP **diminui 4**, virando `0x0028FF7C`
- O valor `1` é colocado na stack

**Valor final:** ESP aponta para `0x0028FF7C`

```
Antes do PUSH 1:          Depois do PUSH 1:
ESP > 0x0028FF80          0x0028FF80
                    ESP > 0x0028FF7C  [valor: 00000001]
```



## Exemplo Prático: POP

**Valor inicial:** após o `PUSH 1`, o ESP aponta para `0x0028FF7C`

**Processo:** o programa executa `POP EAX`
- O valor (`00000001`) contido no endereço do ESP (`0x0028FF7C` - topo da stack) é retirado
- Esse valor é copiado para o registrador **EAX**
- O ESP é atualizado **somando 4**, virando `0x0028FF80`

**Valor final:** ESP aponta para `0x0028FF80` - retornou ao valor original

```
Antes do POP EAX:                    Depois do POP EAX:
ESP > 0x0028FF7C [00000001]          0x0028FF7C
      0x0028FF80                ESP > 0x0028FF80
                                      EAX = 00000001
```



## Resumo

| Operação | ESP | Efeito |
|----------|-----|--------|
| **PUSH** | ESP - 4 (ou -8) | Adiciona dado ao topo, stack cresce |
| **POP** | ESP + 4 (ou +8) | Remove dado do topo, stack encolhe |

