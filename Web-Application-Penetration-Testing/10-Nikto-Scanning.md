

## O que é Nikto?

O Nikto é um **scanner de web server open-source** que realiza testes abrangentes contra servidores web, procurando por diversas categorias de problemas.

---

## O que o Nikto verifica

- Configurações inseguras do servidor
- Versões desatualizadas de software com vulnerabilidades conhecidas
- Arquivos e programas potencialmente perigosos
- Headers HTTP de segurança ausentes ou mal configurados
- Arquivos de instalação padrão que não foram removidos
- Diretórios e arquivos sensíveis expostos

---

## Uso básico

```bash
# Scan básico
nikto -h http://target.com

# Scan em porta específica
nikto -h http://target.com -p 8080

# Scan com SSL
nikto -h https://target.com

# Salvar output em arquivo
nikto -h http://target.com -o report.html -Format htm
```

---

## Observações

- O Nikto é **bastante ruidoso** e não é uma ferramenta stealth
- Gera grande volume de requisições ao servidor
- Ideal para **identificação rápida** de problemas óbvios de configuração
- Os resultados devem ser **validados manualmente** e podem haver falsos positivos

