# HTML Smuggling
 
## O que é
 
HTML smuggling é uma técnica pra entregar payloads maliciosos escondidos dentro de HTML e JavaScript, passando por defesas de rede como firewalls, proxies e gateways de e-mail sem ser detectado.
 
A ideia: o payload não viaja como um arquivo executável que seria barrado pelos controles de segurança. Ele viaja como código HTML/JavaScript aparentemente inofensivo e só é montado no lado do cliente, dentro do navegador da vítima.
 
---
 
## Como funciona
 
### 1. Embutir o conteúdo malicioso
 
O atacante codifica o payload (geralmente em base64) e embute dentro de um elemento HTML ou JavaScript. Pode ser dividido em pedaços menores que são remontados no lado do cliente.
 
### 2. Entrega
 
O HTML malicioso é entregue por e-mail (corpo HTML ou anexo) ou através de um site comprometido. Como o payload está escondido dentro de HTML, ferramentas de segurança que escaneiam anexos e tráfego web buscando assinaturas de malware não detectam.
 
### 3. Reconstrução e execução
 
Quando o HTML chega no navegador da vítima, o JavaScript decodifica e remonta o payload. O resultado pode ser a execução de scripts maliciosos, download automático de arquivos ou redirecionamento pra páginas de phishing.
 
---
 
## Por que é eficaz
 
- **Bypass de controles de rede** - o payload não existe como arquivo durante o trânsito. Ele é montado no endpoint, depois de passar por todas as camadas de defesa
- **Difícil de detectar** - pra ferramentas de segurança, é só HTML/JavaScript normal. Sem assinatura de malware pra flagrar
- **Entrega flexível** - funciona via e-mail e via web, os dois vetores mais comuns de ataque client-side
---
 
## Contexto no ataque
 
HTML smuggling é uma técnica de **entrega**, não de exploração. É o mecanismo que faz o payload chegar até o alvo sem ser interceptado. Uma vez no navegador da vítima, o payload precisa de outro vetor pra execução (engenharia social, exploit de navegador, etc.).
 
Faz parte da fase de **Delivery** da Cyber Kill Chain.
 
---
 
## Referências
 
- [MITRE ATT&CK — HTML Smuggling](https://attack.mitre.org/techniques/T1027/006/)
- [Unified Cyber Kill Chain](https://www.unifiedkillchain.com/)
---
