

## O que é OWASP Amass?

O OWASP Amass é um **framework de reconhecimento automatizado** que combina diversas técnicas para mapear a superfície de ataque de uma organização. É uma das ferramentas mais completas para enumeração de ativos externos.

---

## Funcionalidades principais

- Enumeração de subdomínios (passiva e ativa)
- Resolução DNS em massa
- Mapeamento de infraestrutura e rede
- Integração com múltiplas fontes de dados (APIs, certificados SSL, etc.)
- Geração de grafos de relacionamento entre ativos
- Monitoramento contínuo de alterações

---

## Uso básico

```bash
# Enumeração de subdomínios
amass enum -d example.com

# Enumeração passiva apenas (sem interagir com o alvo)
amass enum -passive -d example.com

# Salvar resultados em arquivo
amass enum -d example.com -o results.txt

# Enumeração com brute-force ativo
amass enum -brute -d example.com
```

---

## Por que usar?

O Amass agrega resultados de **dezenas de fontes** em uma única ferramenta, economizando tempo e aumentando a cobertura da fase de reconhecimento. É especialmente útil para organizações com grande superfície de ataque.

