# Windows Credential Manager e cmdkey



## Windows Credential Manager

O Windows Credential Manager é uma funcionalidade nativa do Windows que permite ao usuário guardar e gerenciar credenciais de forma "segura" nomes de usuário, senhas e outras informações de login para serviços, aplicações, sites e recursos de rede.

Ele faz parte do ecossistema de segurança do Windows e existe pra simplificar a autenticação: em vez de o usuário digitar a senha toda vez que acessa um recurso, o Credential Manager guarda e reutiliza a credencial automaticamente. Do ponto de vista de usabilidade, ótimo. Do ponto de vista ofensivo, é um cofre de credenciais esperando pra ser aberto.



## cmdkey

`cmdkey` é um utilitário de linha de comando do Windows que interage com o Credential Manager. Ele permite gerenciar as credenciais guardadas direto pelo terminal, o que dá flexibilidade e automação no manuseio delas.

Com o `cmdkey` você consegue:

- **Adicionar** credenciais
- **Listar** credenciais
- **Deletar** credenciais

### Listando o que está guardado

O comando mais útil na fase de enumeração é o de listagem:

```cmd
cmdkey /list
```

Isso mostra todas as credenciais armazenadas no Credential Manager do usuário atual. O detalhe: o `cmdkey /list` mostra que as credenciais **existem** e para quais alvos (o campo `Target`), mas não exibe a senha em texto claro.



## Como isso vira escalação

Saber que existe uma credencial guardada para, por exemplo, uma conta administrativa é metade do caminho. A outra metade é usá-la sem precisar da senha em claro. É aí que entra o `runas` com a flag `/savecred`:

```cmd
runas /savecred /user:ADMIN\Administrator "cmd.exe /c <comando>"
```

Quando uma credencial administrativa está salva no Credential Manager, o `runas /savecred` reutiliza essa credencial guardada para executar um comando **no contexto daquela conta** sem que a gente precise conhecer a senha. Se a credencial salva for de um usuário privilegiado, isso entrega escalação direta.

O fluxo mental é:

```
cmdkey /list          > descobre QUE credenciais estão guardadas
runas /savecred       > USA a credencial guardada sem saber a senha
```

Esse par é um dos vetores mais limpos de escalação no Windows quando o ambiente tem credencial administrativa cacheada coisa comum em máquinas de administradores preguiçosos ou em setups de automação mal pensados.

