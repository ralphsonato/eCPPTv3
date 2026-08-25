# Hash Cracking


## NT / NTLM

O hash mais comum em ambientes Windows. Obtido via SAM dump, secretsdump, Mimikatz ou responder.

```bash
# john
john hash.txt --wordlist=rockyou.txt --format=NT
john hash.txt --show --format=NT

# hashcat (modo 1000)
hashcat -m 1000 hash.txt wordlist.txt --force

# hashcat com regras (expande cobertura sem wordlist maior)
hashcat -m 1000 hash.txt wordlist.txt -r /usr/share/hashcat/rules/best64.rule --force

# formato do hash: hash puro sem prefixo
echo "cf7771248bde3fabc95ca491d47e9108" > ntlm.hash
```

---

## AS-REP Roasting - Kerberos 5 TGT

Obtido via `impacket-GetNPUsers` contra contas com `UF_DONT_REQUIRE_PREAUTH`.

```bash
# john
john hash.txt --wordlist=rockyou.txt --format=krb5asrep

# hashcat (modo 18200)
hashcat -m 18200 hash.txt wordlist.txt --force

# formato do hash: começa com $krb5asrep$23$
```

---

## Kerberoasting - Kerberos 5 TGS

Obtido via `impacket-GetUserSPNs` contra contas com SPN.

```bash
# john
john hash.txt --wordlist=rockyou.txt --format=krb5tgs

# hashcat (modo 13100)
hashcat -m 13100 hash.txt wordlist.txt --force
```

---

## DCC2 - Domain Cached Credentials

Encontrado em `lsadump::cache` ou no output do secretsdump como `$DCC2$`. Mais lento que NTLM mas crackeia offline sem DC.

```bash
# hashcat (modo 2100)
echo '$DCC2$10240#administrator#b0e03ef855a6fec78512ec09511c22a7' > dcc2.hash
hashcat -m 2100 dcc2.hash wordlist.txt --force

# john
john dcc2.hash --wordlist=rockyou.txt --format=mscash2
```

---

## KeePass

Obtido via `keepass2john` a partir do arquivo `.kdbx`.

```bash
# Converte para formato john
keepass2john database.kdbx > keepass.hash

# john
john keepass.hash --wordlist=rockyou.txt

# hashcat (modo 13400) - precisa remover o prefixo com nome do arquivo
cat keepass.hash | sed 's/NomeDoArquivo://' > kp_hashcat.hash
hashcat -m 13400 kp_hashcat.hash wordlist.txt --force
hashcat -m 13400 kp_hashcat.hash wordlist.txt -r /usr/share/hashcat/rules/best64.rule --force
```

> ⚠️ KeePass com 50.000 iterações é muito lento (120 H/s em CPU). Prioriza wordlists pequenas e certeiras antes de partir para rockyou.

---

## MD5 - WordPress / aplicações web

```bash
# john
john hash.txt --wordlist=rockyou.txt --format=raw-md5
john hash.txt --show --format=raw-md5

# hashcat (modo 0)
hashcat -m 0 hash.txt wordlist.txt --force

# verificar se uma senha específica gera o hash
echo -n 'senha' | md5sum
```

---

## Regras do hashcat - quando a wordlist não é suficiente

Regras aplicam transformações nas palavras da wordlist (capitalização, substituições, sufixos). Aumentam cobertura sem precisar de wordlist maior.

```bash
# best64 - mais rápido, cobre os padrões mais comuns
hashcat -m 1000 hash.txt wordlist.txt -r /usr/share/hashcat/rules/best64.rule --force

# combinator - combina duas wordlists
hashcat -m 1000 hash.txt -a 1 wordlist1.txt wordlist2.txt --force

# listar regras disponíveis
ls /usr/share/hashcat/rules/
```

---

## Tabela de referência rápida

| Tipo | Modo hashcat | Formato john | Velocidade |
|------|-------------|--------------|------------|
| NT/NTLM | 1000 | NT | Muito rápida |
| AS-REP | 18200 | krb5asrep | Rápida |
| Kerberoast | 13100 | krb5tgs | Rápida |
| DCC2 | 2100 | mscash2 | Média |
| KeePass 2 | 13400 |   | Lenta |
| MD5 | 0 | raw-md5 | Muito rápida |

