

## Como funciona o Stored XSS

No Stored XSS, o payload malicioso é:

1. **Enviado para o servidor** (via comentário, post, perfil, etc.)
2. **Armazenado no banco de dados** do servidor
3. **Servido a todos os usuários** que acessam a página contendo o payload
4. **Executado no navegador** de cada vítima que visita a página

---

## Diferença do Reflected XSS

| Aspecto | Reflected XSS | Stored XSS |
|---------|--------------|------------|
| Persistência | Não persiste | Fica armazenado no servidor |
| Alcance | Apenas quem clica no link | Todos que visitam a página |
| Gravidade | Menor | **Maior** |
| Interação necessária | Vítima precisa clicar em link | Vítima só precisa visitar a página |

---

## Exemplo prático (MyBB Forum)

O curso demonstra a exploração de vulnerabilidades Stored XSS em um fórum MyBB, onde é possível injetar scripts maliciosos através de posts ou campos de perfil que são renderizados sem sanitização para todos os usuários do fórum.

---

## Locais comuns onde encontrar Stored XSS

- Seções de comentários
- Posts de fórum
- Campos de perfil de usuário
- Mensagens privadas
- Reviews e avaliações
- Nomes de arquivo em uploads
- Campos de formulário que são exibidos em dashboards administrativos

---

## Impacto

O Stored XSS é considerado **mais perigoso** que o Reflected porque:

- Afeta múltiplas vítimas automaticamente
- Não requer engenharia social para cada vítima
- Pode ser usado para ataques em massa
- Persiste até ser removido do banco de dados

