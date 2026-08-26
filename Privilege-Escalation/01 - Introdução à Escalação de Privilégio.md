# Introdução à Escalação de Privilégio



## O que é

Escalação de privilégio é o processo de conseguir acesso elevado ou privilégios adicionais dentro de um sistema ou rede, tipicamente sair de um usuário de baixo nível para um usuário de nível mais alto ou administrador. Na prática, é explorar vulnerabilidades ou misconfigurations para chegar a recursos que normalmente estariam restritos a contas com mais permissão do que a que a gente tem em mãos.

É um dos conceitos centrais de pentest e red teaming porque o acesso inicial quase nunca vem no nível que a gente precisa. Comprometi um serviço web e caí como `www-data`? Isso não me dá acesso aos hashes do sistema, não me deixa instalar persistência decente e não me abre caminho pra movimentação lateral com credencial privilegiada. A escalação é o que fecha essa lacuna.



## Os dois tipos: vertical e horizontal

A escalação se divide em dois tipos, e a diferença entre eles é sobre *o quê* muda quando você escala.

### Vertical

O atacante sobe de um usuário de menor privilégio para um de maior privilégio. É a escalação "clássica": sair de um usuário comum e virar administrador (Windows) ou root (Linux).

Exemplo: num Linux, o atacante consegue partir de um usuário/aplicação sem privilégio e chegar a root.

### Horizontal

O atacante mantém o mesmo nível de privilégio, mas assume a identidade de outro usuário. Aqui ele **não ganha** privilégio adicional, só passa a agir como outra conta do mesmo patamar.

Exemplo: num Windows, o atacante assume a identidade de qualquer outro usuário Standard do sistema. Ele continua sendo um usuário Standard, não virou Administrator só trocou de "pele".

O ponto que costuma confundir é achar que horizontal é inútil. Não é. Assumir a identidade de outro usuário do mesmo nível pode dar acesso a arquivos, credenciais ou recursos que a conta original não tinha, e isso frequentemente vira o trampolim pra uma escalação vertical depois.



## Onde isso encaixa na engagement

Escalação é uma atividade de **pós-exploração**. Ela pressupõe que você já tem um pé dentro do sistema. O fluxo típico é:

```
Acesso inicial (shell de usuário comum)
        
Enumeração local (entender o sistema, achar misconfigurations)
        
Escalação de privilégio (virar SYSTEM / root)
        
Credential access, persistência, movimentação lateral
```

A enumeração é o pré-requisito silencioso de tudo aqui. Você não escala o que não enxerga, a maior parte do trabalho de privesc é achar a misconfiguration certa, não executar o exploit.

