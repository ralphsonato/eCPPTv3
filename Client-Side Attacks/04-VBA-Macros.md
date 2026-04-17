# VBA Macros

## O que é VBA

VBA (Visual Basic for Applications) é a linguagem de programação da Microsoft pra automação dentro do Office - Excel, Word, PowerPoint, Access, Outlook. Permite criar macros que automatizam tarefas, manipulam dados e interagem com o sistema operacional.

O problema: essa mesma funcionalidade que facilita a vida do usuário legítimo é a que o atacante usa pra executar código malicioso.

---

## Macros na prática

Uma macro é simplesmente um pedaço de código VBA embutido dentro de um documento Office. Macros foram amplamente usadas como vetor de ataque desde os anos 90, quando eram executadas automaticamente ao abrir um documento.

### Evolução da segurança

- **Antes de 2003** - macros executavam automaticamente. Vírus de macro eram epidemia
- **A partir de 2003** - macros não executam mais automaticamente. Usuário vê um aviso de segurança
- **A partir de 2007** - formatos novos (DOCX, XLSX) não suportam macros. Pra embutir macro, precisa usar DOCM, XLSM, etc.

### Formatos de arquivo

| Extensão | Tipo | Permite macro? |
|---|---|---|
| .docx | Documento comprimido | Não |
| .dotx | Template comprimido | Não |
| .docm | Documento comprimido | Sim |
| .dotm | Template comprimido | Sim |

Detalhe importante: um arquivo DOCM pode ser renomeado pra .rtf e o Word ainda vai abrir e executar as macros. A validação do Office é baseada na estrutura interna do arquivo, não na extensão.

---

## WScript e VBA

WScript (Windows Script Host) é o motor de scripts do Windows. Dentro do VBA, podemos criar instâncias do WScript pra executar comandos no sistema, manipular arquivos, rodar programas externos - basicamente escapar do sandbox do Office e interagir com o SO.

Isso é o que torna macros VBA perigosas: a ponte entre o documento Office e o sistema operacional.

---

## Macros em ataques client-side

### Como são usadas

**Mecanismo de entrega** - o documento com macro é o veículo. Chega por e-mail, download, USB. O alvo abre e habilita macros.

**Engenharia social** - o documento precisa convencer o alvo a clicar em "Habilitar Conteúdo". Pretexting visual dentro do documento (mensagem falsa de erro, instrução pra habilitar macros).

**Exploração de vulnerabilidades** - macros interagem com ActiveX, Windows API e objetos COM pra executar código arbitrário.

**Entrega de payload** - a macro é só o primeiro estágio. Ela baixa e executa o payload real (reverse shell, dropper, loader) de um servidor remoto.

---

## ActiveX Controls

ActiveX são componentes interativos da Microsoft (botões, caixas de texto, media players) que podem ser embutidos em documentos Office. O ponto relevante: eles executam código.

### Por que usar ActiveX em vez de AutoOpen

Os procedimentos `AutoOpen()` e `Document_Open()` são os métodos clássicos pra execução automática de macros - e por isso são os primeiros que antivírus procuram.

ActiveX controls oferecem uma alternativa: em vez de executar automaticamente, o código roda quando o usuário interage com o controle (clicar num botão, focar num campo). Isso contorna detecções baseadas nos nomes reservados.

Existe uma lista grande de eventos ActiveX que podem disparar macros automaticamente (como `InkEdit1_GotFocus`). Cada controle tem suas próprias sub-rotinas que podem ser usadas pra execução.

---

## MacroPack

Ferramenta open source em Python 3 pra automatizar a criação e ofuscação de macros maliciosas.

### O que faz

- Gera macros prontas pra uso em pentests e red teaming
- Ofusca automaticamente o código (renomeia funções, variáveis, remove comentários, codifica strings)
- Suporta múltiplos formatos de saída

### Formatos suportados

**Scripting**: .vba, .vbs, .wsf, .hta

**MS Office**: .doc, .docm, .docx, .dotm, .xls, .xlsm, .xlsx, .xltm, .pptm, .potm, .accdb, .mdb

### Referência

[MacroPack no GitHub](https://github.com/sevagas/macro_pack)

---

