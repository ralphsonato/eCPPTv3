

## O que é?

Web Server Fingerprinting é o processo de **identificar o tipo e versão do web server** que está hospedando a aplicação alvo. Essa informação é essencial para buscar vulnerabilidades conhecidas (CVEs) associadas àquela versão específica.

---

## Técnicas de Fingerprinting

### Análise de Headers HTTP

Os headers de resposta HTTP frequentemente revelam informações sobre o servidor:

```
Server: Apache/2.4.49 (Ubuntu)
X-Powered-By: PHP/7.4.3
```

**Como verificar manualmente:**
```bash
curl -I https://example.com
```

### Comportamento do Servidor

Diferentes servidores web respondem de formas distintas a requisições específicas (como requisições malformadas ou métodos HTTP incomuns). Ferramentas automatizadas usam essas diferenças para identificar o servidor.

---

## Ferramentas

- **Nmap** - com scripts NSE para HTTP
  ```bash
  nmap -sV -p 80,443 target.com
  ```
- **WhatWeb** - fingerprinting detalhado
- **Netcraft** - via web
- **Burp Suite** - análise de headers nas respostas interceptadas

