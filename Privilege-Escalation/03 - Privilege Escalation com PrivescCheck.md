# Privilege Escalation com PrivescCheck



## O que é

PrivescCheck é outra ferramenta em PowerShell para enumeração de vetores de escalação no Windows. A ideia é a mesma do PowerUp, automatizar a caça a misconfigurations, mas ela funciona como uma alternativa mais moderna e ativamente mantida.

Na prática, vale rodar as duas: elas se complementam. O PowerUp é o clássico consagrado, mas por ser mais antigo pode não pegar configurações de versões recentes do Windows; o PrivescCheck tende a cobrir cenários mais atuais e apresenta os resultados de forma organizada, separando os achados por severidade.



## O que ela cobre

O PrivescCheck varre categorias parecidas com as do PowerUp, mas com um leque mais amplo de checagens:

- Serviços com permissões fracas e unquoted service paths
- Permissões de arquivo e de registro que permitem modificação indevida
- Tarefas agendadas exploráveis
- Credenciais armazenadas (Credential Manager, arquivos de configuração, unattended files)
- Configurações de UAC
- Aplicações e drivers vulneráveis conhecidos
- Informações sensíveis expostas no ambiente



## Como usar na prática

```powershell
# Importa e roda a checagem
powershell -ep bypass
Import-Module .\PrivescCheck.ps1

# Verificação padrão
Invoke-PrivescCheck

# Com relatório mais detalhado / exportável
Invoke-PrivescCheck -Extended -Report PrivescCheck_report -Format HTML,TXT
```

O modo estendido com relatório é útil na hora de documentar a engagement, ele gera um arquivo com todos os achados organizados, o que economiza tempo na fase de reporte.



## PowerUp vs PrivescCheck

Não é "um ou outro". A recomendação prática é rodar ambos e cruzar os resultados:

| | PowerUp | PrivescCheck |
|---|---------|--------------|
| Framework | Parte do PowerSploit | Standalone |
| Manutenção | Mais antigo | Ativamente mantido |
| Cobertura | Vetores clássicos | Vetores clássicos + modernos |
| Saída | Texto no console | Console + relatório (HTML/TXT) por severidade |



## Referências

- PrivescCheck: https://github.com/itm4n/PrivescCheck

