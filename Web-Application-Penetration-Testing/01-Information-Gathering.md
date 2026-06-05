
## O que é Information Gathering?

A coleta de informações é a **primeira etapa** de qualquer pentest. Consiste em reunir o máximo de dados possíveis sobre o alvo, seja uma pessoa, empresa, website ou sistema.

Quanto mais informações coletadas nesta fase, maiores serão as chances de sucesso nas fases seguintes do teste.

**Ponto importante:** não existe informação desnecessária. Tudo que for coletado deve ser registrado e salvo para uso futuro.

No contexto de pentest de aplicações web, as informações desta fase ajudam a entender a **lógica e a estrutura** da aplicação, o que será fundamental durante a fase de exploração.

---

## Tipos de Coleta de Informações

| Tipo | Descrição | Autorização? |
|------|-----------|-------------|
| **Passiva** | Coletar informações sem interagir diretamente com o alvo | Não |
| **Ativa (Enumeração)** | Coletar informações interagindo diretamente com o sistema alvo | Sim |

---

## Que tipo de informação estamos procurando?

- Propriedade do website e domínio
- Endereços IP, domínios e subdomínios
- Arquivos e diretórios ocultos
- Infraestrutura de hospedagem (web server, CMS, banco de dados, etc.)
- Presença de soluções defensivas como WAF (Web Application Firewall)

---

## Coleta Passiva - O que buscar

- Identificação de domínios e informações de propriedade
- Descoberta de arquivos/diretórios ocultos ou bloqueados (ex: `robots.txt`)
- Identificação de endereços IP do web server e registros DNS
- Identificação das tecnologias web utilizadas no site alvo
- Detecção de WAF
- Identificação de subdomínios
- Mapeamento da estrutura de conteúdo do website

---

## Coleta Ativa - O que buscar

- Download e análise do código-fonte da aplicação web
- Port scanning e descoberta de serviços
- Fingerprinting do web server
- Scanning da aplicação web
- DNS Zone Transfers
- Enumeração de subdomínios via brute-force

