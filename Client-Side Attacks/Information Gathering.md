# Information Gathering & Fingerprinting
 
## Por que isso importa
 
O sucesso de um ataque client-side depende diretamente da qualidade da informação coletada sobre o alvo. Não adianta mandar um exploit pra Chrome se o cara usa Firefox. Não adianta mandar macro pra Office se o alvo usa LibreOffice.
 
Antes de montar o payload, você precisa saber o que roda do outro lado.
 
---
 
## Passiva vs Ativa
 
Assim como no pentest tradicional, a coleta de informações se divide em duas abordagens:
 
**Passiva** - você não interage diretamente com o alvo. Coleta informações de fontes públicas sem deixar rastro.
 
**Ativa** - você interage com o alvo ou sistema dele pra extrair informações. Deixa rastro, mas consegue dados mais precisos.
 
---
 
## Coleta passiva
 
### OSINT
 
Vasculhar fontes abertas pra montar o perfil do alvo e da organização:
 
- LinkedIn, Twitter e redes sociais em geral - cargos, relações, tecnologias mencionadas
- Site da empresa - stack tecnológica, vagas de emprego (revelam ferramentas internas)
- Fóruns e comunidades - discussões técnicas sobre a organização
**Ferramentas**: Google Dorks, Maltego, theHarvester.
 
### Reconhecimento via buscadores
 
Usar operadores avançados de busca pra descobrir informações expostas publicamente sobre alvos, sistemas e infraestrutura.
 
**Ferramentas**: Google Search operators, Shodan, DuckDuckGo.
 
---
 
## Coleta ativa
 
### Client Fingerprinting
 
Técnica pra descobrir o navegador, versão, plugins, SO e arquitetura do sistema do alvo. Essencial pra construir payloads sob medida.
 
O fluxo é:
 
1. Comprar um domínio e subir uma página falsa (mas convincente)
2. Embutir JavaScript na página que coleta informações do navegador
3. Usar engenharia social pra fazer o alvo visitar a página
4. O script roda no navegador do alvo e envia os dados pra você
**O que queremos identificar**: navegador e versão, plugins/extensões, SO, versão do SO, arquitetura do sistema.
 
**Ferramenta**: [fingerprintjs2](https://github.com/LukasDrgon/fingerprintjs2) - biblioteca JavaScript que enumera informações detalhadas do navegador e SO.
 
**Limitação**: depende do navegador do alvo executar JavaScript. Navegadores focados em privacidade podem bloquear.
 
### Engenharia social como coleta
 
Interagir diretamente com funcionários por telefone, e-mail ou mensagem pra extrair informações sobre software e configurações internas.
 
**Ferramentas**: SET (Social-Engineer Toolkit), BeEF (Browser Exploitation Framework).
 
---
 
## Exemplo prático: o golpe do currículo
 
Cenário do curso que mostra como engenharia social e fingerprinting se combinam:
 
1. Alice (pentester) encontra uma vaga aberta na Acme Corp com upload de currículo
2. Cria persona falsa "Sarah Johnson" e envia currículo com macro que simula erro ao abrir
3. RH da Acme tenta abrir, falha, e responde pedindo reenvio
4. Alice responde e, de forma inocente, pergunta: *"Qual versão do Word vocês usam? Quero garantir compatibilidade"*
5. RH responde com a versão do Word - sem imaginar que acabou de entregar informação crítica
6. Alice agora sabe o software exato e pode construir um payload sob medida
Simples, elegante e eficaz. Nenhuma vulnerabilidade técnica explorada — só o fator humano.
 
---
