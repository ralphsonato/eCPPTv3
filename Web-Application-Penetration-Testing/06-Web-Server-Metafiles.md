
## O que são Metafiles?

São arquivos de metadados presentes em servidores web que fornecem instruções para crawlers e bots. Esses arquivos podem **revelar informações valiosas** sobre a estrutura do site, incluindo diretórios e páginas que os administradores preferem manter ocultos.

---

## Arquivos importantes para verificar

### robots.txt

Arquivo que instrui crawlers de mecanismos de busca sobre quais diretórios/páginas **não devem ser indexados**.

```
# Exemplo de robots.txt
User-agent: *
Disallow: /admin/
Disallow: /backup/
Disallow: /config/
Disallow: /private/
```

> **Importante:** O `robots.txt` é apenas uma **sugestão** para crawlers legítimos. Qualquer pessoa pode acessar os paths listados diretamente no navegador.

**Como acessar:**
```
https://example.com/robots.txt
```

### sitemap.xml

Arquivo XML que lista todas as páginas do site que devem ser indexadas. Pode revelar paths e estrutura do site.

```
https://example.com/sitemap.xml
```

### Outros metafiles

- `.htaccess` - configurações do Apache
- `crossdomain.xml` - políticas de acesso entre domínios (Flash)
- `security.txt` - informações de contato de segurança
- `humans.txt` - informações sobre a equipe

---

## Por que verificar metafiles?

Os paths listados no `Disallow` do `robots.txt` são frequentemente **diretórios sensíveis** que os administradores não querem que apareçam em buscas, mas que podem conter informações úteis para o pentest.

