

## O que é?

Consiste em tentar acessar paths que **não são visíveis** na navegação normal do site, utilizando wordlists com nomes comuns de diretórios e arquivos. A ferramenta faz requisições HTTP para cada path da wordlist e analisa os códigos de resposta para determinar se o recurso existe.

---

## Ferramentas

### Gobuster
Rápido, escrito em Go.
```bash
gobuster dir -u http://target.com -w /usr/share/wordlists/dirb/common.txt
```

### Dirb
Clássico, simples de usar.
```bash
dirb http://target.com /usr/share/wordlists/dirb/common.txt
```

### ffuf
Muito rápido e flexível.
```bash
ffuf -u http://target.com/FUZZ -w /usr/share/wordlists/dirb/common.txt
```

### Dirsearch
Python, bastante flexível.
```bash
dirsearch -u http://target.com -w /path/to/wordlist.txt
```

---

## O que procurar

- Painéis administrativos (`/admin`, `/administrator`, `/login`, `/wp-admin`)
- Arquivos de backup (`.bak`, `.old`, `.swp`, `.zip`)
- Arquivos de configuração (`.env`, `config.php`, `web.config`)
- Diretórios de upload (`/uploads`, `/files`, `/media`)
- APIs não documentadas (`/api`, `/v1`, `/v2`)
- Páginas de debug ou desenvolvimento (`/debug`, `/test`, `/dev`)

---

## Códigos de resposta HTTP importantes

| Código | Significado | Ação |
|--------|------------|------|
| **200** | OK - o recurso existe | Investigar |
| **301/302** | Redirect | Seguir o redirect |
| **403** | Forbidden - existe mas sem permissão | Recurso existe, tentar bypass |
| **404** | Not Found | Não existe |
| **500** | Internal Server Error | Possível vulnerabilidade |

