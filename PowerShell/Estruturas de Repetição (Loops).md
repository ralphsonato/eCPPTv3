## Estruturas de Repetição (Loops)

### Tipos de loop disponíveis

| Estrutura | Descrição |
|-----------|-----------|
| `for()` | Loop clássico com contador |
| `foreach()` | Itera sobre cada item de uma coleção |
| `while()` | Executa enquanto a condição for verdadeira |
| `do {} while()` | Executa ao menos uma vez, repete enquanto condição for verdadeira |
| `do {} until()` | Executa ao menos uma vez, repete até que a condição seja verdadeira |

### Obtendo ajuda sobre loops

```powershell
Get-Help about_Foreach
Get-Help about_For
Get-Help about_Do
Get-Help about_While
```

### Exemplo: foreach com serviços

```powershell
# Armazenar serviços em uma variável
$services = Get-Service

# Iterar e exibir o nome de cada serviço
foreach ($service in $services) {
    $service.Name
}
```

### Mesmo resultado usando ForEach-Object com pipeline

```powershell
Get-Service | ForEach-Object { $_.Name }
```

> `$_` representa o **objeto atual** no pipeline.

### Filtrando com Where-Object

```powershell
# Listar apenas arquivos que contenham "xls" no nome
Get-ChildItem C:\Dados\ | Where-Object { $_.Name -match "xls" }
```

### Exemplo prático: Scanner de Portas TCP

Este é um scanner simples de portas que pode ser executado como one-liner
ou salvo em um arquivo `.ps1`:

```powershell
# One-liner
$ports = (80, 443, 8080, 22)
$ip = "192.168.1.100"

foreach ($port in $ports) {
    try {
        $socket = New-Object System.Net.Sockets.TcpClient($ip, $port)
    } catch {}

    if ($socket -eq $null) {
        echo "$ip`:$port - Fechada"
    } else {
        echo "$ip`:$port - Aberta"
        $socket = $null
    }
}
```

> Salve como `Scanner-Portas.ps1` e execute com `.\Scanner-Portas.ps1`

---
