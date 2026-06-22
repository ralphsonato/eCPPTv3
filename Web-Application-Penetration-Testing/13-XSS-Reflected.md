

## O que é XSS?

Cross-Site Scripting (XSS) ocorre quando uma aplicação web inclui dados não confiáveis em uma página **sem validação ou sanitização adequada**, permitindo a execução de scripts maliciosos no navegador da vítima.

---

## XSS Refletido - Como funciona

No Reflected XSS, o payload malicioso é:

1. **Enviado na requisição** (geralmente via parâmetro URL ou campo de formulário)
2. **Refletido na resposta** do servidor sem ser sanitizado
3. **Executado no navegador** da vítima

### Características

- **Não é persistente** - afeta apenas a sessão atual
- Requer que a vítima **clique em um link malicioso** contendo o payload
- O servidor não armazena o payload, apenas o reflete de volta

---

## Exemplo prático (WordPress)

O curso demonstra a exploração de vulnerabilidades Reflected XSS em instalações WordPress, onde parâmetros de busca ou outros inputs são refletidos na página sem sanitização.

---

## Impacto

- Roubo de cookies de sessão
- Redirecionamento para sites maliciosos
- Keylogging
- Defacement da página para o usuário afetado
- Phishing direcionado

---

## Como testar

1. Identificar todos os pontos de input da aplicação (URL params, formulários, headers)
2. Inserir payloads de teste simples como `<script>alert(1)</script>`
3. Verificar se o payload é refletido na resposta sem ser sanitizado
4. Se refletido, testar se é executado no navegador

---

## Ferramentas

- Burp Suite (scanner + testing manual via Repeater/Intruder)
- OWASP ZAP
- XSStrike
