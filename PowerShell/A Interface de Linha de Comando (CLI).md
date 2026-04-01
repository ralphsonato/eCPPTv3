# A Interface de Linha de Comando (CLI)

### Como acessar o PowerShell

Existem diversas formas de abrir o PowerShell:

1. **Pesquisa do Windows:** digitar `powershell` na barra de pesquisa do Menu Iniciar.
2. **Atalho:** localizado em `%appdata%\Microsoft\Windows\Start Menu\Programs\Windows PowerShell`
3. **Executável direto:** `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`

### Diferença entre 32-bit e 64-bit

Em sistemas 64-bit, a localização pode causar confusão:

| Arquitetura | Caminho |
|------------|---------|
| 64-bit | `C:\Windows\System32\WindowsPowerShell\` |
| 32-bit | `C:\Windows\SysWOW64\WindowsPowerShell\` |

Para verificar se o processo atual é 64-bit:

```powershell
[Environment]::Is64BitProcess
# Retorna True se for 64-bit
```

> **Dica:** Sempre que possível, execute o PowerShell como **Administrador** (clique
> direito → "Executar como Administrador") para ter acesso a funções privilegiadas.

### Parâmetros importantes do powershell.exe

Estes parâmetros são usados ao chamar o PowerShell a partir do `cmd.exe` ou de
outro contexto:

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `-ExecutionPolicy Bypass` | Ignora a política de execução de scripts | `powershell.exe -ep Bypass .\script.ps1` |
| `-ExecutionPolicy Unrestricted` | Permite execução sem restrições | `powershell.exe -ex Unrestricted .\script.ps1` |
| `-WindowStyle Hidden` | Oculta a janela do PowerShell | `powershell.exe -W Hidden .\script.ps1` |
| `-Command` | Executa um comando ou bloco de script | `powershell.exe -Command Get-Process` |
| `-EncodedCommand` | Executa um comando codificado em Base64 | `powershell.exe -ec $encodedCmd` |
| `-NoProfile` | Não carrega perfis de inicialização | `powershell.exe -NoProfile .\script.ps1` |
| `-Version` | Força uma versão específica do PowerShell | `powershell.exe -Version 2` |

> **Observação:** Os parâmetros podem ser abreviados desde que sejam únicos,
> e não são case-sensitive. Ex: `-ep` para `-ExecutionPolicy`, `-W h` para
> `-WindowStyle Hidden`.

### Obtendo ajuda: Get-Help

O cmdlet `Get-Help` funciona como as man pages do Linux:

```powershell
# Ajuda básica sobre um cmdlet
Get-Help Get-Process

# Ajuda completa com detalhes de todos os parâmetros
Get-Help Get-Process -Full

# Apenas exemplos de uso
Get-Help Get-Process -Examples

# Abrir a página de ajuda online no navegador
Get-Help Get-Process -Online

# Atualizar arquivos de ajuda locais
Update-Help
```

### Descobrindo comandos: Get-Command

O cmdlet `Get-Command` lista todos os cmdlets, aliases, funções e scripts disponíveis:

```powershell
# Listar todos os comandos disponíveis
Get-Command

# Filtrar comandos por nome (ex: relacionados a Firewall)
Get-Command -Name *Firewall*
```

---
