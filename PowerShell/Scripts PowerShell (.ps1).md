## Scripts PowerShell (.ps1)

### Estrutura básica

Scripts PowerShell são arquivos `.ps1` que podem conter desde comandos simples
até funções complexas com parâmetros, loops e lógica condicional.

### Executando um script

```powershell
# Executar um script no diretório atual
.\meu_script.ps1

# Se a política de execução bloquear, usar bypass
powershell.exe -ExecutionPolicy Bypass .\meu_script.ps1
```

### Exemplo: script que lê um arquivo

```powershell
# exemplo.ps1
param(
    [Parameter(Mandatory=$true)]
    [string]$file
)

Get-Content $file
```

**Uso:**

```powershell
.\exemplo.ps1 -file usuarios.txt
# ou simplesmente
.\exemplo.ps1 usuarios.txt
```

Se executado sem argumentos e `Mandatory=$true` estiver definido, o PowerShell
solicitará o valor interativamente.

### Alternativa rápida (direto no shell)

```powershell
$file = "usuarios.txt"
Get-Content $file
```

---
