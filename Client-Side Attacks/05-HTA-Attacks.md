# HTML Applications (HTA)
 
## O que são
 
HTAs (HTML Applications) são aplicações escritas em HTML, CSS e JavaScript que rodam fora do navegador, como programas standalone no Windows. Usam a extensão `.hta` e são executadas pelo `mshta.exe`.
 
A diferença crucial: enquanto uma página HTML no navegador roda dentro de um sandbox com restrições de segurança, um HTA roda com acesso privilegiado ao sistema - pode ler/escrever arquivos, executar comandos, acessar o registro e interagir com ActiveX.
 
---
 
## mshta.exe
 
É o Microsoft HTML Application Host - o executável do Windows responsável por rodar arquivos HTA.
 
### O que ele faz
 
- Interpreta e executa o HTML/CSS/JavaScript do arquivo HTA
- Fornece um ambiente de execução fora do navegador
- Dá acesso privilegiado ao sistema (filesystem, registro, comandos do SO)
- Está sujeito às configurações de zona de segurança do Internet Explorer
### Por que isso é relevante pra ataques
 
HTAs executados via mshta.exe rodam com o contexto de segurança do usuário atual e não passam pelo sandbox do navegador. Isso significa que o JavaScript dentro de um HTA pode fazer tudo que o usuário logado pode fazer no sistema.
 
---
 
## HTA em ataques client-side
 
### Execução de código arbitrário
 
Salvar um arquivo como `.hta` em vez de `.html` faz com que o Internet Explorer (ou mshta.exe diretamente) execute o conteúdo com privilégios elevados. Isso transforma JavaScript comum em uma ferramenta capaz de executar comandos no SO.
 
### Por que ainda funciona
 
Pode parecer estranho depender do Internet Explorer em 2024, mas:
 
- Muitas organizações e ambientes corporativos ainda usam IE como navegador padrão
- Versões enterprise do Windows frequentemente mantém IE ativo
- mshta.exe vem instalado por padrão no Windows - não precisa do IE estar aberto
### Capacidades de scripting
 
O JavaScript dentro de um HTA pode:
 
- Baixar e executar payloads de servidores remotos
- Modificar configurações do sistema
- Coletar informações sensíveis
- Interagir com ActiveX controls
### Persistência e evasão
 
HTAs são arquivos standalone que rodam fora do navegador, o que facilita:
 
- Execução persistente no sistema da vítima
- Ofuscação do código pra evadir antivírus
- Uso como mecanismo de entrega combinado com engenharia social
### Classificação MITRE
 
Ataques via HTA são tipicamente classificados como **Drive-by Compromise** - o código executa automaticamente quando o alvo interage com o arquivo.
 
---
 
## Referências
 
- [MITRE ATT&CK — Mshta](https://attack.mitre.org/techniques/T1218/005/)
- [Cyber Kill Chain — Lockheed Martin](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)
---
