# Social Engineering

## O que é

Engenharia social é a arte de manipular pessoas pra que façam algo que comprometa a segurança - revelar informações, clicar em links, abrir arquivos, dar acesso. Explora psicologia humana, não vulnerabilidades técnicas.

No contexto de pentest e red teaming, simula ameaças reais pra testar a postura de segurança da organização atacando o elo mais fraco: as pessoas.

---

## Por que funciona

Engenharia social explora instintos básicos:

- Desejo de ajudar
- Tendência a confiar
- Busca por aprovação
- Medo de se encrencar
- Aversão a conflitos

Com isso, o atacante não precisa passar pela segurança técnica. Ele convence alguém de dentro a fazer o trabalho por ele. Minutos de engenharia social podem render o que horas de brute force não conseguiriam.

---

## Redes sociais como acelerador

Redes sociais mudaram o jogo. Qualquer pessoa do mundo pode entrar em contato com funcionários de qualquer empresa. E as próprias pessoas expõem e-mails, telefones, cargos, rotinas e preferências sem perceber que estão montando um dossiê sobre si mesmas.

---

## Tipos de ataques

| Técnica | Descrição |
|---|---|
| **Phishing** | E-mails falsos com links ou anexos maliciosos, simulando fontes confiáveis |
| **Spear Phishing** | Phishing direcionado e personalizado pra alvos específicos |
| **Vishing** | Phishing por voz — ligações simulando suporte técnico, banco, etc. |
| **Smishing** | Phishing por SMS |
| **Pretexting** | Criar um cenário falso pra ganhar confiança e extrair informações |
| **Baiting** | Oferecer isca (software grátis, prêmio, vaga de emprego) pra induzir uma ação |
| **Tailgating** | Entrar fisicamente em áreas restritas seguindo atrás de alguém autorizado |

---

## Phishing em detalhe

O ataque de engenharia social mais usado. Funciona assim:

1. **Planejamento e reconhecimento** - pesquisar o alvo, entender canais de comunicação, protocolos internos
2. **Construção da mensagem** - criar e-mail que imita comunicação legítima (colega, TI, banco). Linguagem urgente pra forçar ação rápida
3. **Entrega** - enviar contornando filtros de spam e controles de segurança
4. **Engano** - alvo clica no link, baixa o anexo ou fornece credenciais
5. **Exploração** - payload executa, credenciais são capturadas, acesso é obtido

---

## Spear Phishing

A diferença pro phishing genérico: aqui tudo é personalizado.

O atacante pesquisa o alvo a fundo — nome, cargo, projetos, relações, interesses — e monta uma mensagem sob medida. Referencia eventos recentes, usa nomes de colegas reais, simula contexto legítimo.

O processo:

1. **Seleção e pesquisa do alvo** - cargos, hierarquia, redes sociais, diretórios corporativos, dados vazados
2. **Personalização da mensagem** - conteúdo específico pro alvo, referenciando atividades e projetos reais. Pode se passar por colega, chefe ou parceiro
3. **Entrega** - via e-mail, redes sociais, mensageiros. Usa técnicas pra burlar filtros (contas comprometidas, spoofing, zero-days)

---

## Pretexting

Pretexting é criar um cenário falso convincente pra ganhar a confiança do alvo e extrair informações. Não é só mentir — é construir uma narrativa completa.

### Características

- **Pretexto falso** - história fictícia que justifica o contato e o pedido de informação
- **Construção de confiança** - espelhar linguagem, tom e comportamento do alvo pra criar conexão
- **Manipulação emocional** - explorar curiosidade, medo, urgência ou empatia
- **Coleta de informação** - uma vez com confiança, pedir dados sensíveis sob pretexto legítimo
- **Consistência** - manter a história coerente durante toda a interação

### Exemplos clássicos

**Golpe do suporte técnico** - se passar por suporte de empresa legítima, dizer que o computador do alvo está infectado e pedir acesso remoto.

**Golpe da entrevista de emprego** - se passar por recrutador de empresa conhecida, oferecer vaga falsa e pedir dados pessoais ou pagamento.

**Situação de emergência** - fabricar uma emergência (breach, vazamento, queda de sistema) e pedir ação urgente do funcionário pra "resolver".

### Template de pretexting

O curso mostra um template de pretexting corporativo: atacante se passa por alguém do TI e envia e-mail dizendo que o sistema de e-mail está sendo atualizado, pedindo que o funcionário clique em um link pra "atualizar as configurações". O link leva a um portal clonado do Office 365 que captura credenciais.

---
