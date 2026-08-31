# PowerShell History



## A ideia

Esse é um dos vetores mais subestimados e ao mesmo tempo mais eficazes de escalação no Windows. O PowerShell, por padrão, guarda um histórico de todos os comandos que foram digitados numa sessão. Isso é conveniência pura pra quem usa o console no dia a dia mas também significa que, se alguém já digitou uma senha, uma connection string, uma chave de API ou qualquer segredo direto na linha de comando, esse valor ficou registrado em texto claro num arquivo no disco.

É o tipo de descuido que administrador comete o tempo todo: passar credencial como parâmetro de um comando, achando que "some" quando fecha o terminal. Não some vai pro histórico.



## Onde o histórico fica

O módulo `PSReadLine` do PowerShell grava o histórico neste caminho por padrão:

```
C:\Users\<usuário>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt
```

Pra ler direto:

```powershell
Get-Content (Get-PSReadlineOption).HistorySavePath
```

Ou, se você quer o caminho manualmente:

```cmd
type %userprofile%\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt
```



## O que caçar dentro do histórico

O ouro aqui são comandos que envolveram credenciais. Alguns padrões que valem grep:

- `net use` com senha inline
- `Invoke-Command` / `New-PSSession` com `-Credential` construído a partir de senha em texto
- `ConvertTo-SecureString` com senha em plaintext (padrão comum e péssimo)
- Comandos com `-Password`, `-Pass`, `-p`, connection strings de banco
- Qualquer chamada de script que recebeu uma senha como argumento

O padrão do `ConvertTo-SecureString` é especialmente comum:

```powershell
$pass = ConvertTo-SecureString "SenhaEmClaro123" -AsPlainText -Force
```

Quando você acha algo assim no histórico, a senha está literalmente ali, sem nenhum esforço de exploração.



## Por que isso importa

Não tem exploit, não tem CVE, não tem misconfiguration técnica complexa é só um arquivo de texto que ninguém lembrou de limpar. E ainda por cima, o histórico persiste entre sessões, então um comando digitado semanas atrás continua lá. Na fase de enumeração pós-acesso, ler o `ConsoleHost_history.txt` de cada usuário acessível é um dos primeiros movimentos que valem o tempo.

