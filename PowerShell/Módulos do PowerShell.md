## Módulos do PowerShell

### O que são módulos?

Módulos são conjuntos de funcionalidades do PowerShell agrupados em um arquivo
(geralmente com extensão **`.psm1`**). Podem conter scripts, cmdlets, assemblies,
arquivos de ajuda e um manifesto.

### Tipos de módulos

| Tipo | Descrição |
|------|-----------|
| Script Module | O mais comum; contém scripts .ps1 |
| Binary Module | Compilado como assembly .NET |
| Manifest Module | Define metadados e dependências |
| Dynamic Module | Criado em tempo de execução com `New-Module` |

### Gerenciando módulos

```powershell
# Ver módulos atualmente importados na sessão
Get-Module

# Ver todos os módulos disponíveis para importação
Get-Module -ListAvailable

# Importar um módulo
Import-Module .\modulo.psm1

# Ver o caminho padrão de módulos
$Env:PSModulePath
```

### Exemplo prático: PowerSploit

O **PowerSploit** é um framework ofensivo popular escrito em PowerShell.

**Passos para instalação:**

1. Baixar o repositório: https://github.com/PowerShellMafia/PowerSploit
2. Verificar os caminhos de módulos com `$Env:PSModulePath`
3. Copiar os arquivos para um diretório de módulos
   (ex: `C:\users\user\Documents\WindowsPowerShell\Modules\PowerSploit`)
4. Importar no PowerShell:

```powershell
Import-Module PowerSploit
Get-Module  # Verificar se foi importado

# Listar todos os cmdlets do PowerSploit
Get-Command -Module PowerSploit

# Obter ajuda sobre um cmdlet específico
Get-Help Write-HijackDLL
```

> **Atenção:** Frameworks ofensivos como o PowerSploit serão detectados pela maioria
> dos antivírus. Para fins de estudo, crie uma pasta de exclusão no seu AV.

---
