# Privilege Escalation - Anotações de Estudo (eCPPT)

Depois de conseguir o acesso inicial num sistema (seja via exploração de serviço, phishing ou qualquer outro vetor), quase nunca esse acesso vem com o nível de privilégio que a gente precisa. Escalar privilégio é o passo que transforma um shell de usuário comum num shell de `SYSTEM` no Windows ou `root` no Linux, e é aí que o comprometimento vira algo realmente útil.

O foco aqui é entender os vetores clássicos de escalação local nos dois sistemas: no Windows, abuso de serviços mal configurados, registry autoruns, impersonation de tokens, bypass de UAC e DLL hijacking: no Linux, binários SUID, permissões SUDO mal configuradas e injeção de shared library. Cada técnica vem com a lógica por trás do porquê ela funciona, não só o comando.

---



## Objetivos de aprendizado

- Entender o conceito de escalação de privilégio e sua importância em pentest e red teaming
- Identificar misconfigurations e falhas comuns em ambientes Windows e Linux
- Conduzir enumeração de sistema para achar oportunidades de escalação
- Aplicar técnicas de escalação em Windows (serviços inseguros, token impersonation, etc.)
- Aplicar técnicas de escalação em Linux (SUID, SUDO, shared object injection)
- Usar técnicas avançadas: DLL hijacking, bypass de UAC, shared object injection


