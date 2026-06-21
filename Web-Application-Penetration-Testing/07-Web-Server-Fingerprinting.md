

## O que é Technology Fingerprinting?

É o processo de **identificar as tecnologias** utilizadas em uma aplicação web, CMS, frameworks, linguagens de programação, bibliotecas JavaScript, servidores web, etc.

Saber quais tecnologias o alvo utiliza permite direcionar os ataques para vulnerabilidades específicas daquelas versões/tecnologias.

---

## Ferramentas para Fingerprinting

### Wappalyzer
- Extensão de navegador (Chrome/Firefox)
- Identifica automaticamente tecnologias ao navegar no site
- Mostra CMS, frameworks, analytics, CDN, etc.

### BuiltWith
- Ferramenta web que analisa a stack tecnológica de um site
- [builtwith.com](https://builtwith.com)

### WhatWeb (CLI)
- Ferramenta de linha de comando
- Identifica CMS, plataforma de blog, bibliotecas JS, servidor web, dispositivos embarcados, etc.
```bash
whatweb example.com
```

### Extensão de Developer Tools do Navegador
- Inspecionar headers de resposta HTTP
- Analisar código-fonte da página
- Verificar cookies e suas propriedades

---

## O que procurar

- Versão do CMS (WordPress, Joomla, Drupal)
- Framework backend (Django, Laravel, Express, ASP.NET)
- Bibliotecas JavaScript e suas versões
- Servidor web e versão (Apache, Nginx, IIS)
- Linguagem de programação (PHP, Python, Java, .NET)
- Banco de dados (MySQL, PostgreSQL, MSSQL)
- CDN utilizado (Cloudflare, Akamai)
- WAF presente

