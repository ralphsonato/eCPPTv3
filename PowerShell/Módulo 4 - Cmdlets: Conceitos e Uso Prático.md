## Cmdlets: Conceitos e Uso Prático

### O que são Cmdlets?

Cmdlets são os comandos nativos do PowerShell. Suas principais características:

- São scripts leves que executam uma **função específica**.
- São instâncias de **classes do .NET Framework**.
- Seguem o padrão de nomenclatura **Verbo-Substantivo** (ex: `Get-Process`,
  `Set-Location`, `Invoke-Command`).
- Retornam **objetos** (não texto puro), que podem ser processados via pipeline.
- Cada cmdlet possui seus próprios **parâmetros**, que podem ser consultados com
  `Get-Help`.

### Saída padrão vs. saída completa

Por padrão, os cmdlets retornam apenas algumas colunas. Para ver **todas as
propriedades** de um objeto:

```powershell
# Saída padrão (colunas limitadas)
Get-ChildItem

# Saída completa em formato de lista
Get-ChildItem | Format-List *
```

### Aliases (apelidos)

Muitos cmdlets possuem aliases para facilitar a digitação:

```powershell
# Descobrir aliases de um cmdlet
Get-Alias -Definition Get-ChildItem
# Resultado: dir, gci, ls

# Aliases comuns
# ls       → Get-ChildItem
# cd       → Set-Location
# select   → Select-Object
# fl       → Format-List
# %        → ForEach-Object
# sls      → Select-String
```

---
