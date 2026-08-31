# Arquivos de Instalação Não Assistida (Unattended)



## O problema

O Windows consegue automatizar tarefas repetitivas, e uma das mais comuns é o rollout em massa: instalar/implantar o Windows em muitas máquinas de uma vez. Isso normalmente é feito com o utilitário **Unattended Windows Setup**, que automatiza a instalação em larga escala.

Pra funcionar sem interação humana, essa ferramenta usa arquivos de configuração que carregam configurações específicas e **credenciais de contas de usuário** em particular, a senha da conta Administrator.

O problema de segurança é simples: se esses arquivos de configuração ficarem no sistema depois que a instalação termina, eles revelam credenciais que um atacante pode usar pra se autenticar no alvo de forma totalmente legítima. Não precisa explorar nada é só ler o arquivo e usar a senha.



## Onde procurar

O Unattended Windows Setup normalmente usa um destes arquivos de configuração, que contêm dados de conta e de sistema:

```
C:\Windows\Panther\Unattend.xml
C:\Windows\Panther\Autounattend.xml
```

Outros caminhos que também vale checar dependendo do ambiente:

```
C:\Windows\Panther\Unattend\Unattend.xml
C:\Windows\System32\Sysprep\Unattend.xml
C:\Windows\System32\Sysprep\Panther\Unattend.xml
```



## Detalhe importante: base64

Como precaução de segurança, as senhas guardadas no arquivo de configuração do Unattended Setup podem estar **codificadas em base64**. Codificação não é criptografia é reversível trivialmente. Então quando você achar algo parecido com uma senha em base64 no `<Password>`, é só decodificar:

```bash
# No Linux
echo "U2VuaGFDb2RpZmljYWRh" | base64 -d

# No PowerShell
[System.Text.Encoding]::UTF8.GetString([System.Convert]::FromBase64String("U2VuaGFDb2RpZmljYWRh"))
```

Um detalhe que costuma pegar quem está começando: a string em base64 no arquivo unattend frequentemente vem com a palavra `Password` concatenada no final antes de codificar. Depois de decodificar, é comum ver a senha real seguida do texto "Password" grudado é só descartar esse sufixo.



## Por que isso funciona

O ponto forte desse vetor é que ele não depende de exploração de vulnerabilidade nenhuma. É pura higiene ruim: o administrador esqueceu de limpar os arquivos de provisionamento depois do deploy. A credencial obtida costuma ser de conta administrativa (afinal, é a senha usada pra configurar a máquina), o que muitas vezes entrega escalação direta.

