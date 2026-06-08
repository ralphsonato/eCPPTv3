# HTB Machines - Guia de Preparação Prática eCPPTv3



![Status](https://img.shields.io/badge/Status-Em_Progresso-yellow?style=for-the-badge)
![Certificação](https://img.shields.io/badge/Foco-eCPPTv3_INE-orange?style=for-the-badge)
![Total](https://img.shields.io/badge/Total-35_Máquinas-blue?style=for-the-badge)
![Feitas](https://img.shields.io/badge/Feitas-5-green?style=for-the-badge)



> Baseado nos domínios oficiais da INE Security para a certificação eCPPTv3

---

## Domínios Oficiais eCPPTv3

| Domínio | Peso |
|---|---|
| Active Directory Penetration Testing | 30% |
| Exploitation & Post-Exploitation | 25% |
| Initial Access | 15% |
| Web Application Penetration Testing | 15% |
| Information Gathering & Reconnaissance | 10% |
| Exploit Development | 5% |

---

## 🔴 Prioridade Máxima - Active Directory (30%)

> O maior peso do exame. Dominar essas máquinas é obrigatório.

| # | Máquina | Dificuldade | Técnicas | Status |
|---|---|---|---|---|
| 1 | **Forest** | Easy | AS-REP Roasting, BloodHound, DCSync | ✅ Feita |
| 2 | **Active** | Easy | Kerberoasting, GPP Password, SMB Enum | ✅ Feita |
| 3 | **Sauna** | Easy | AS-REP Roasting, DCSync, LDAP Enum | ✅ Feita |
| 4 | **Resolute** | Medium | LDAP Enum, Password Spray, DnsAdmins | ⏳ Pendente |
| 5 | **Monteverde** | Easy | Password Spray, Azure AD Connect | ✅ Feita |
| 6 | **Fuse** | Medium | Password Spray, SeLoadDriver, Printer Enum | ⏳ Pendente |
| 7 | **Cascade** | Medium | LDAP Enum, .NET Reversing, AD Recycle Bin | ✅ Feita |

---

## 🔴 Prioridade Máxima - Exploitation & Post-Exploitation (25%)

> Segundo maior peso. Privesc Linux e Windows, dump de hashes, credenciais locais.

| # | Máquina | OS | Dificuldade | Técnicas | Status |
|---|---|---|---|---|---|
| 8 | **Magic** | Linux | Easy | SQLi, File Upload Bypass, PATH Hijacking | ⏳ Pendente |
| 9 | **OpenAdmin** | Linux | Easy | Known CVE, Port Forwarding, GTFOBins | ⏳ Pendente |
| 10 | **Traverxec** | Linux | Easy | Known CVE RCE, SSH Key Cracking, GTFOBins | ⏳ Pendente |
| 11 | **Traceback** | Linux | Easy | Webshell, SSH motd Abuse, Sudo PrivEsc | ⏳ Pendente |
| 12 | **Haystack** | Linux | Easy | Kibana LFI CVE, Logstash PrivEsc | ⏳ Pendente |
| 13 | **Teacher** | Linux | Medium | Moodle RCE, MySQL, Symlink Misconfiguration | ⏳ Pendente |
| 14 | **Tabby** | Linux | Easy | Tomcat WAR Deploy, ZIP Cracking, LXD | ⏳ Pendente |
| 15 | **Curling** | Linux | Easy | CMS Enum, Credential Reuse, Cron Job | ⏳ Pendente |
| 16 | **Bart** | Windows | Medium | Log Poisoning, Pass-the-Hash, SMB Enum | ⏳ Pendente |
| 17 | **Chaos** | Linux | Medium | Restricted Shell Escape, Firefox Profile | ⏳ Pendente |
| 18 | **Nest** | Windows | Easy | SMB Enum, Credential Reuse, Source Code Review | ⏳ Pendente |
| 19 | **Lightweight** | Linux | Medium | Linux Capabilities Abuse | ⏳ Pendente |

---

## 🟠 Prioridade Alta - Initial Access (15%)

> Username enum, password spray, brute force, cobrado na inicial de acesso.

| # | Máquina | OS | Dificuldade | Técnicas | Status |
|---|---|---|---|---|---|
| 20 | **Netmon** | Windows | Easy | PRTG CVE, Anonymous FTP, Credential Leak | ⏳ Pendente |
| 21 | **Heist** | Windows | Easy | Cisco Hash Cracking, RID Brute Force | ⏳ Pendente |
| 22 | **Help** | Linux | Easy | GraphQL Enum, Blind SQLi, Kernel Exploit | ⏳ Pendente |
| 23 | **FluxCapacitor** | Linux | Medium | HTTP Parameter Fuzzing, WAF Bypass | ⏳ Pendente |
| 24 | **Luke** | Linux | Medium | Node.js API Enum, JWT, Credential Reuse | ⏳ Pendente |

---

## 🟠 Prioridade Alta - Web Application Pentest (15%)

> SQLi, XSS, Command Injection, componentes vulneráveis, direto nos objetivos da INE.

| # | Máquina | OS | Dificuldade | Técnicas | Status |
|---|---|---|---|---|---|
| 25 | **Sniper** | Windows | Medium | LFI/RFI, PHP Session Abuse, CHM Attack | ⏳ Pendente |
| 26 | **Sense** | Linux | Easy | PFSense CVE, RCE, Service Exploitation | ⏳ Pendente |
| 27 | **Book** | Linux | Medium | XSS, LFI, Log Poisoning, SQL Truncation | ⏳ Pendente |
| 28 | **RedCross** | Linux | Medium | XSS, SQLi, OS Command Injection | ⏳ Pendente |
| 29 | **Wall** | Linux | Medium | HTTP Verb Tampering, WAF Bypass, Centreon CVE | ⏳ Pendente |
| 30 | **Stratosphere** | Linux | Medium | Apache Struts CVE, RCE | ⏳ Pendente |
| 31 | **Unattended** | Linux | Medium | SQLi, LFI to RCE | ⏳ Pendente |

---

## 🟡 Prioridade Média - Exploit Development (5%)

> Buffer Overflow aparece nos objetivos da INE. Pequeno peso mas presente.

| # | Máquina | OS | Dificuldade | Técnicas | Status |
|---|---|---|---|---|---|
| 32 | **Enterprise** | Linux | Hard | WordPress Plugin, Docker, Buffer Overflow | ⏳ Pendente |

---

## 🟢 Recomendado - Pivoting & Tunneling

> Pivoting não aparece como domínio oficial da eCPPTv3 mas é essencial para CNPen e CPTS.

| # | Máquina | OS | Dificuldade | Técnicas | Status |
|---|---|---|---|---|---|
| 33 | **Inception** | Linux | Medium | LFI, SSRF, Pivoting, SSH Tunneling | ⏳ Pendente |
| 34 | **Vault** | Linux | Medium | Pivoting, OpenVPN Malicioso, SSH Port Forwarding | ⏳ Pendente |
| 35 | **Hawk** | Linux | Medium | Drupal CVE, SSH Tunneling | ⏳ Pendente |

---

## 📊 Progresso Geral

| Domínio | Máquinas | Feitas | Pendentes |
|---|---|---|---|
| 🔴 Active Directory (30%) | 7 | 5 | 2 |
| 🔴 Exploitation & Post-Exploit (25%) | 12 | 0 | 12 |
| 🟠 Initial Access (15%) | 5 | 0 | 5 |
| 🟠 Web Application (15%) | 7 | 0 | 7 |
| 🟡 Exploit Development (5%) | 1 | 0 | 1 |
| 🟢 Pivoting | 3 | 0 | 3 |
| **Total** | **35** | **5** | **30** |

---

<div align="center">
  <a href="https://www.linkedin.com/in/ralph-sonato-77086b16b/">
    <img src="https://img.shields.io/badge/LinkedIn-Ralph_Sonato-0e76a8?style=for-the-badge&logo=linkedin&logoColor=white">
  </a>
</div>
