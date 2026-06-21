
## Crawling

### O que é?

Crawling é o processo de **navegar pela aplicação web** seguindo links, enviando formulários e fazendo login (quando possível), com o objetivo de mapear e catalogar a aplicação e seus caminhos de navegação.

### Características

- Geralmente considerado **passivo**, a interação é feita via o que está publicamente acessível
- Objetivo: entender como a aplicação está estruturada e como ela funciona
- Ajuda a construir um mapa completo do site

### Ferramenta principal

**Burp Suite** - possui um passive crawler que mapeia automaticamente a aplicação enquanto você navega pelo site com o proxy configurado.

---

## Spidering

### O que é?

Spidering é o processo de **descoberta automática de novos recursos** (URLs) em uma aplicação web.

### Como funciona

1. Começa com uma lista de URLs iniciais chamadas **seeds**
2. O spider visita cada URL e identifica hyperlinks na página
3. Adiciona os novos links encontrados à lista de URLs para visitar
4. Repete o processo **recursivamente** até não encontrar mais links novos

### Características

- Considerado **ativo** por ser bastante ruidoso e gerar grande volume de tráfego
- Pode disparar alertas em WAFs e sistemas de monitoramento
- Mais abrangente que o crawling manual

### Ferramenta principal

**OWASP ZAP** - possui um Spider integrado que automatiza todo o processo de mapeamento da aplicação.

---

## Diferença entre Crawling e Spidering

| Aspecto | Crawling | Spidering |
|---------|----------|-----------|
| Tipo | Passivo | Ativo |
| Volume de tráfego | Baixo | Alto |
| Automatização | Semi-automático | Totalmente automático |
| Ferramenta | Burp Suite | OWASP ZAP |
| Risco de detecção | Baixo | Alto |

---
