
## O que é DNS?

O **Domain Name System (DNS)** é o protocolo responsável por resolver nomes de domínio/hostnames para endereços IP. Funciona como uma "lista telefônica" da internet, ao invés de memorizar IPs, digitamos nomes de domínio que são traduzidos automaticamente.

**Servidores DNS públicos populares:**
- Cloudflare: `1.1.1.1`
- Google: `8.8.8.8`

---

## Por que o DNS é importante no pentest?

Depois de coletar informações iniciais sobre o alvo, podemos consultar o DNS para **mapear a infraestrutura** do site. Isso ajuda a construir uma topologia do alvo e entender como os diferentes componentes estão conectados.

---

## Tipos de Registros DNS

| Registro | Função |
|----------|--------|
| **A** | Resolve hostname/domínio para endereço IPv4 |
| **AAAA** | Resolve hostname/domínio para endereço IPv6 |
| **NS** | Referência ao nameserver do domínio |
| **MX** | Resolve domínio para servidor de e-mail |
| **CNAME** | Alias de domínio (aponta um domínio para outro) |
| **TXT** | Registro de texto (SPF, DKIM, verificação de domínio) |
| **HINFO** | Informações do host |
| **SOA** | Start of Authority — autoridade do domínio |
| **SRV** | Registros de serviço |
| **PTR** | Resolve endereço IP para hostname (DNS reverso) |

---

## Enumeração DNS Passiva

Consultar registros DNS usando fontes **públicas**, sem interagir diretamente com o servidor DNS do alvo.

**Ferramentas e fontes:**
- DNSDumpster
- VirusTotal
- SecurityTrails
- `nslookup` / `dig` (consultando servidores públicos)

**Exemplos de comandos:**
```bash
# Consultar registro A
dig A example.com

# Consultar todos os registros
dig ANY example.com

# Consultar MX records
dig MX example.com

# Usando nslookup
nslookup -type=any example.com
```

---

## Enumeração DNS Ativa

Interação direta com o servidor DNS do alvo.

**DNS Zone Transfer:**
```bash
dig axfr @ns.example.com example.com
```

**Brute-force de subdomínios:**
- Sublist3r
- Amass
- Fierce

