# Privilege Escalation com PowerUp



## O que é

PowerUp é uma das ferramentas mais usadas no contexto de escalação de privilégio no Windows. Ela faz parte do framework **PowerSploit**, uma coleção de ferramentas em PowerShell voltadas pra tarefas ofensivas: enumeração, exploração e pós-exploração. Dentro desse conjunto, o PowerUp é o cara focado em identificar vetores comuns de escalação num ambiente Windows.

O valor dele está na automação. Em vez de checar manualmente dezenas de configurações do sistema atrás de brechas, o PowerUp roda uma bateria de verificações e te devolve os pontos fracos já mapeados.

---

## O que o PowerUp verifica

Ele automatiza o scan de um sistema Windows atrás de misconfigurations, vulnerabilidades e falhas de segurança que possam abrir caminho pra escalação. As checagens que ele faz cobrem os vetores mais recorrentes:

- **Insecure Service Configurations** - serviços rodando com privilégio elevado (ex: `SYSTEM`) que estão vulneráveis por causa de permissões fracas ou outros problemas de segurança.
- **Unquoted Service Paths** - serviços com caminho de executável sem aspas, que podem ser explorados colocando um executável malicioso num ponto estratégico do caminho.
- **Weak Registry Permissions** - chaves de registro com permissões inseguras que permitem modificação não autorizada, levando à escalação.
- **Vulnerable Scheduled Tasks** - tarefas agendadas que podem ser manipuladas pra rodar com privilégio elevado.
- **Insecure File Permissions** - arquivos ou diretórios com permissões fracas que dá pra explorar pra executar código com privilégio mais alto.
- **Insecure DLL Search Orders** - ordens de busca de DLL exploráveis, que abrem espaço pra DLL hijacking. 
- **Stored Credentials** - credenciais guardadas de forma insegura em chaves de registro, arquivos ou outros lugares.

---

## Como usar na prática

O fluxo padrão é importar o script no PowerShell e rodar a checagem completa:

```powershell
# Importa o módulo
powershell -ep bypass
Import-Module .\PowerUp.ps1

# Roda todas as verificações de uma vez
Invoke-AllChecks
```

O `Invoke-AllChecks` é o comando-chave: ele dispara todas as verificações e mostra os vetores encontrados, geralmente já sugerindo o abuso possível pra cada achado.

---

## Referências

- PowerUp: https://github.com/PowerShellMafia/PowerSploit/blob/master/Privesc/PowerUp.ps1

