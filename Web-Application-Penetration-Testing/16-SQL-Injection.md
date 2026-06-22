

## O que é SQL Injection?

SQL Injection (SQLi) ocorre quando um atacante consegue **inserir código SQL malicioso** em consultas que a aplicação envia ao banco de dados, devido à falta de validação ou sanitização dos inputs do usuário.

---

## Taxonomia de SQL Injection

```
SQL Injection
├── In-Band SQLi
│   ├── Error-Based SQLi
│   └── Union-Based SQLi
├── Blind SQLi
│   ├── Boolean-Based SQLi
│   └── Time-Based SQLi
└── Out-of-Band SQLi
```

---

## In-Band SQL Injection

É o tipo **mais comum** de SQL injection. O atacante utiliza o **mesmo canal de comunicação** para enviar o ataque e receber os resultados.

O payload é injetado via requisição HTTP e os dados extraídos aparecem na resposta HTTP.

### Fluxo

1. Atacante envia payload SQLi via requisição HTTP
2. Web server processa e envia a query SQL ao banco de dados
3. Banco de dados executa a query e retorna os dados
4. Web server retorna os dados ao atacante na resposta HTTP

### Impacto

- Roubo de informações sensíveis
- Modificação ou exclusão de dados
- Tomada de controle da aplicação web inteira
- Possível comprometimento do servidor

---

## Ferramentas para encontrar SQLi

- **OWASP ZAP** - scanner automatizado que pode detectar vulnerabilidades de SQLi
- **Burp Suite** - interceptação e modificação manual de requisições
- **SQLMap** - ferramenta automatizada para exploração de SQLi




