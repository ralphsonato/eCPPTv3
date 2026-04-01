## Pipelining (Encadeamento de Comandos)

### Como funciona

O pipeline (`|`) permite encadear cmdlets, passando a **saída de um como entrada
do próximo**. É semelhante ao pipe do Linux/Bash.

```powershell
# Exemplo: listar processos únicos e exibir apenas o nome
Get-Process | Sort-Object -Unique | Select-Object ProcessName

# Redirecionar a saída para um arquivo
Get-Process | Sort-Object -Unique | Select-Object ProcessName > processos_unicos.txt
```

### Fluxo do exemplo acima:

1. `Get-Process` → retorna todos os processos em execução
2. `Sort-Object -Unique` → remove duplicatas
3. `Select-Object ProcessName` → seleciona apenas a propriedade "ProcessName"

---
