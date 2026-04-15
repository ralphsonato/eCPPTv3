# Introdução a Client-Side Attacks
 
## O que são
 
Ataques client-side exploram vulnerabilidades no lado do cliente - o computador, o navegador, o e-mail, o Office do funcionário. O alvo não é o servidor, é a pessoa.
 
A lógica é simples: em vez de tentar derrubar a porta da frente (servidor), o atacante convence alguém de dentro a abrir a porta pra ele.
 
Esses ataques dependem de algum tipo de interação humana. O payload precisa ser entregue e alguém precisa clicar, abrir, executar. Por isso andam de mãos dadas com engenharia social.
 
---
 
## Por que são tão eficazes
 
Algumas razões que tornam ataques client-side atrativos:
 
- **Superfície de ataque enorme** - desktops, laptops, celulares, tablets... todo dispositivo de endpoint é um alvo em potencial.
- **Fator humano** - exploram curiosidade, confiança e desconhecimento. Pessoas são o elo mais fraco.
- **Controles de segurança mais frouxos** - endpoints geralmente têm menos proteção que servidores e infraestrutura de rede.
- **Porta de entrada pro movimento lateral** - uma vez dentro, o atacante pivota pra outros sistemas, escala privilégios e persiste.
 
---
 
## Client-Side vs Server-Side
 
| | Client-Side | Server-Side |
|---|---|---|
| **Alvo** | Dispositivos e aplicações do usuário final | Servidores, infra de rede, backend |
| **Objetivo** | Comprometer endpoint, roubar dados, ganhar foothold | Acesso não autorizado a servidores, exfiltração, disrupção |
| **Execução** | Entrega de conteúdo malicioso via e-mail, site, documento | Exploração de vulnerabilidades em software/serviço do servidor |
| **Exemplos** | Phishing, drive-by downloads, documentos maliciosos, exploit kits | SQLi, XSS, SSRF, RCE, brute force |
 
---
 
## Como funciona na prática
 
Metodologia típica de um ataque client-side:
 
**Reconhecimento** → pesquisar a organização, identificar funcionários, tecnologias usadas, domínios de e-mail.
 
**Identificação de alvos** → selecionar alvos específicos (financeiro, RH, executivos) com base no reconhecimento.
 
**Desenvolvimento do payload** → criar documento malicioso (Word com macro, PDF com exploit, HTA) adaptado pro software que o alvo usa.
 
**Preparação** → montar o pretexto convincente e a infraestrutura de entrega (site comprometido, domínio falso, file sharing).
 
**Entrega** → enviar phishing pro alvo com o payload anexado ou linkado.
 
**Execução** → quando o alvo interage com o payload, o código malicioso roda. Conexão reversa estabelecida.
 
**Pós-exploração** → escalação de privilégios, movimento lateral, exfiltração. O jogo começa de verdade.
 
---
 
## Vetores de ataque comuns
 
**Engenharia social** - phishing, social media engineering, pretexting, baiting, tailgating. O vetor mais usado e mais eficaz.
 
**Documentos maliciosos** - Word, Excel, PDF com macros, scripts ou exploits embutidos. Abre o arquivo, roda o código.
 
**Drive-by downloads** - sites comprometidos que entregam malware automaticamente quando o alvo visita a página.
 
**Watering hole** - comprometer sites que os alvos frequentam e injetar código malicioso neles.
 
**USB** - espalhar pendrives infectados em locais estratégicos. Plugou, executou.
 
**Exploit kits** - kits automatizados que exploram vulnerabilidades em navegadores e plugins.
 
**Browser exploitation** - explorar vulnerabilidades diretamente no navegador ou extensões pra executar código no sistema da vítima.
 
---
