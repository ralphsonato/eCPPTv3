

## O que é Error-Based SQLi?

É uma técnica que consiste em **forçar erros intencionais no banco de dados** e utilizar as mensagens de erro retornadas para extrair informações sobre a estrutura e o conteúdo do banco.

As mensagens de erro podem revelar nomes de tabelas, colunas, tipos de dados, versão do banco e até dados sensíveis armazenados.

---

## Como funciona

1. O tester envia um **payload SQLi** projetado para causar um erro no banco
2. O DBMS retorna uma **mensagem de erro** ao web server
3. O web server exibe essa mensagem na **resposta HTTP**
4. O tester analisa a mensagem de erro para **extrair informações**

---

## Metodologia passo a passo

### 1. Identificar parâmetro vulnerável

Encontrar inputs que participam de queries SQL:
- Parâmetros de URL (`?id=1`, `?page=home`)
- Campos de formulário
- Cookies
- Headers HTTP

### 2. Injetar código SQL malicioso

Criar payloads que forcem erros no banco de dados. O teste mais básico é inserir uma **aspas simples** `'` no parâmetro:

```
http://target.com/page?id=1'
```

Se o servidor retornar um erro SQL, o parâmetro é provavelmente vulnerável.

### 3. Observar mensagens de erro

Analisar as mensagens de erro retornadas. Elas podem conter:
- Tipo do banco de dados (MySQL, PostgreSQL, MSSQL, etc.)
- Nomes de tabelas e colunas
- Fragmentos da query SQL original
- Informações sobre a estrutura do schema

### 4. Extrair dados

Modificar o payload para obter informações específicas do banco, como:
- Nomes de databases
- Nomes de tabelas
- Nomes de colunas
- Usernames e passwords
- Outros dados sensíveis

### 5. Explorar a vulnerabilidade

Usar as informações coletadas para comprometer a aplicação.

---

## Pré-requisito

Para o Error-Based SQLi funcionar, a aplicação precisa estar **exibindo mensagens de erro** detalhadas do banco de dados na resposta. Se as mensagens de erro forem suprimidas ou genéricas, outras técnicas (como Blind SQLi) serão necessárias.

