## Objetos e Métodos

### Entendendo objetos no PowerShell

Diferente de outros shells que retornam texto puro, o PowerShell retorna **objetos**
derivados de classes .NET. Cada objeto possui:

- **Propriedades:** dados associados ao objeto (ex: `Name`, `Id`, `Path`)
- **Métodos:** ações que podem ser executadas no objeto (ex: `Kill`, `Start`)

### Visualizando propriedades

```powershell
# Ver todas as propriedades de processos
Get-Process | Format-List *
```

### Descobrindo métodos disponíveis

```powershell
# Listar métodos dos objetos retornados por Get-Process
Get-Process | Get-Member -MemberType Method
```

### Exemplo: encerrar um processo usando método

```powershell
# Encerrar todos os processos do Firefox
Get-Process -Name "firefox" | Kill
```

**Fluxo lógico:**

1. Identificar o objeto de interesse (`Get-Process`)
2. Descobrir os métodos disponíveis (`Get-Member`)
3. Aplicar o método desejado via pipeline (`Kill`)

---

