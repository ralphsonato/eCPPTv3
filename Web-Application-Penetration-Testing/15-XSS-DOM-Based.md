
## Como funciona o DOM-Based XSS

No DOM-Based XSS, o payload é processado **inteiramente no lado do cliente** (navegador), sem que o servidor tenha qualquer participação no ataque.

A vulnerabilidade está na forma como o **JavaScript da página** manipula o DOM (Document Object Model), usando dados controlados pelo usuário de forma insegura.

---

## Fluxo do ataque

1. A vítima acessa uma URL contendo o payload malicioso (geralmente no fragment `#` ou em parâmetros)
2. O JavaScript do lado do cliente lê o input da URL
3. O JavaScript insere o dado no DOM **sem sanitização**
4. O payload é executado no navegador da vítima

---

## Diferença dos outros tipos de XSS

| Aspecto | Reflected | Stored | DOM-Based |
|---------|-----------|--------|-----------|
| Processamento | Servidor | Servidor | **Cliente** |
| Payload no servidor | Sim | Sim | **Não** |
| Visível nos logs do server | Sim | Sim | **Não necessariamente** |

> O servidor pode nunca "ver" o payload — ele é processado apenas no navegador.

---

## Fontes comuns de input (sources)

- `document.URL`
- `document.location`
- `document.referrer`
- `window.location.hash`
- `window.location.search`
- `window.name`

## Sinks perigosos

- `document.write()`
- `innerHTML`
- `eval()`
- `setTimeout()` / `setInterval()` com strings
- `document.location`

---

## Como testar

1. Analisar o código JavaScript do lado do cliente
2. Identificar onde inputs do usuário são lidos (sources)
3. Rastrear como esses inputs fluem até pontos de execução (sinks)
4. Testar se é possível injetar payloads que são executados

