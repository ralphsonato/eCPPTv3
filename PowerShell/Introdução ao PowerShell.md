### O que é o PowerShell?

O PowerShell é um interpretador de linha de comando (shell) e uma linguagem de script
desenvolvida pela Microsoft. Está presente nativamente nos sistemas Windows a partir
do Windows 7 e Windows Server 2008 R2.

**Características principais:**

- É construído sobre o **.NET Framework**, o que significa que temos acesso direto
  a classes e métodos do .NET dentro do shell.
- Oferece acesso ao **COM (Component Object Model)** e ao **WMI (Windows Management
  Instrumentation)**, permitindo interagir profundamente com o sistema operacional.
- Os scripts são identificados pela extensão **`.ps1`** (o "1" refere-se ao engine,
  não à versão).
- Os comandos nativos são chamados de **Cmdlets** (pronuncia-se "command-lets").

### Versões importantes

| Versão | Observação |
|--------|-----------|
| 1.0 / 2.0 | Versões mais antigas, com menos controles de segurança e logging. |
| 5.0+ | Introduziu logging avançado, modo de linguagem restrita (Constrained Language Mode). |
| 6.0+ (Core) | Versão open source e multiplataforma (Linux, macOS, Docker). |

> **Dica de pentest:** Versões mais antigas (1.0, 2.0) possuem menos mecanismos de
> detecção. Se estiverem disponíveis no alvo, pode ser vantajoso fazer downgrade.

**Repositório oficial:** https://github.com/powershell/powershell

---
