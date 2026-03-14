# Subdomain Discovery (Enumeração de Subdomínios)

A enumeração de subdomínios é uma etapa fundamental do reconhecimento em testes de intrusão web. O objetivo é identificar todos os subdomínios associados a um domínio principal para mapear a superfície de ataque real da organização.

Exemplo:

```
empresa.com
app.empresa.com
dev.empresa.com
vpn.empresa.com
mail.empresa.com
intranet.empresa.com
```

Muitas vezes, o domínio principal está bem protegido, mas subdomínios esquecidos, ambientes de homologação ou sistemas legados permanecem expostos.

---

# 1. Coleta Passiva vs Coleta Ativa

## Coleta Passiva

A coleta passiva não interage diretamente com o alvo. Ela utiliza bases públicas, logs de certificados, histórico DNS, mecanismos de busca e serviços OSINT.

Características:

- Não gera tráfego direto ao servidor alvo
    
- Não deixa rastros em logs do servidor
    
- Ideal para fase inicial de reconhecimento
    
- Pode revelar infraestrutura antiga
    

Fontes comuns:

- Certificate Transparency Logs
    
- Histórico DNS
    
- Arquivos históricos da web
    
- APIs públicas
    

---

## Coleta Ativa

A coleta ativa interage diretamente com a infraestrutura do alvo.

Exemplos:

- Brute force DNS
    
- Resolução massiva de nomes
    
- Tentativas de zone transfer
    
- Scan de portas
    

Características:

- Pode gerar logs
    
- Pode disparar WAF, IDS ou firewall
    
- Descobre subdomínios não indexados publicamente
    

---

# 2. Ferramentas e Plataformas Passivas

## SecurityTrails

![Image](https://en.a-parser.com/docs/assets/images/1-32e364e38fbc458e1e59259142cf78ea.png)

![Image](https://netlas.io/blog/dns_history_exploring/securitytrails_a_records_1_hu_bd57d74cfef6682e.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AJrrDuc3DtD8-sBKsE_TLgQ.png)

![Image](https://cdn.readme.io/og-image/create?color=%23000&description=Returns+subdomains+for+a+given+hostname&logoUrl=https%3A%2F%2Ffiles.readme.io%2Ff3e9e5c-small-SecurityTrails-Logo-Black.png&projectTitle=SecurityTrails+Developer+&title=List+Subdomains&type=reference&variant=light)

Site: [https://securitytrails.com](https://securitytrails.com/)

O SecurityTrails é uma plataforma OSINT que fornece:

- Histórico de registros DNS
    
- Subdomínios conhecidos
    
- IPs antigos
    
- Registros A, MX, TXT
    
- Mudanças históricas de apontamento
    

Importância estratégica:

Quando uma empresa contrata um WAF (por exemplo Cloudflare), o DNS passa a apontar para o IP do WAF. Porém, o IP real do servidor pode ter sido público anteriormente e ainda estar registrado no histórico.

Cenário típico:

Antes:

```
empresa.com → 1.2.3.4
```

Depois:

```
empresa.com → IP Cloudflare
```

O IP 1.2.3.4 pode continuar acessível se o administrador não restringiu acesso direto.

Isso permite teste direto ao IP:

```
curl http://IP_REAL -H "Host: empresa.com"
```

Se responder, pode existir bypass do WAF.

---

## DNSDumpster

![Image](https://techofide.com/media/uploads/2023/03/21/9_ZLuPXWS.webp)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AHraRh1BWZk-4F_XCsv37vQ.png)

![Image](https://ceeyu-strapi.ams3.digitaloceanspaces.com/Massdns_10ea29ac16.png)

![Image](https://opengraph.githubassets.com/08ff7b5aec02f0ab8e3c45a13ec6f44c1c4de9001526e68fd15adc8f5fae9b92/nmmapper/dnsdumpster)

Site: [https://dnsdumpster.com](https://dnsdumpster.com/)

Ferramenta online que realiza:

- Enumeração passiva
    
- Mapeamento de servidores DNS
    
- Identificação de subdomínios
    
- Visualização gráfica da infraestrutura
    

É útil para ter uma visão macro da estrutura DNS da organização.

---

## Web Archive (Wayback Machine)

![Image](https://www.lifewire.com/thmb/P-xPUFif6DYA9ifcqfqlz9mccpM%3D/1500x0/filters%3Ano_upscale%28%29%3Amax_bytes%28150000%29%3Astrip_icc%28%29/WayBack-Machine-Search-Bar-b38b8ded832b472499450450ad2a53fb.jpg)

![Image](https://web-static.archive.org/_static/waybackjs/screenshots/wm_yelp.com_20131019024453.png)

![Image](https://eqsash.com/custom/files/images/articles/history-domain-archive-org.jpg)

![Image](https://s3.amazonaws.com/images.seroundtable.com/wayback-machine-1559515797.jpg)

Site: [https://web.archive.org](https://web.archive.org/)

Permite visualizar versões antigas de sites.

Uso estratégico:

- Identificar subdomínios antigos
    
- Encontrar endpoints removidos
    
- Descobrir aplicações descontinuadas
    

Às vezes um subdomínio removido do DNS ainda está ativo internamente.

---

## crt.sh (Certificate Transparency)

![Image](https://raw.githubusercontent.com/az7rb/crt.sh/main/Screenshot/Screenshot_Help.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AFp59Jml9o6PhpMhYfS9dwA.png)

![Image](https://hacklido.com/assets/files/2023-02-03/1675424413-893561-screenshot-68.png)

![Image](https://cdn.hashnode.com/res/hashnode/image/upload/v1731279673339/8f583716-d6db-4520-8505-a765df582355.png)

Site: [https://crt.sh](https://crt.sh/)

Consulta logs públicos de certificados TLS emitidos.

Se foi emitido certificado para:

```
vpn.empresa.com
api.empresa.com
dev.empresa.com
```

Esses registros ficam públicos.

É uma das fontes mais importantes para enumeração passiva.

---

## CertSpotter

![Image](https://opengraph.githubassets.com/fa3dd946c847d857b746c12a98b69464804b0f317ea21cb430817d1315b47a66/SSLMate/certspotter)

![Image](https://sslmate.com/img/home/unknown_issuance_email_cropped.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/0%2A3YgMwQRBTct0LeUd.png)

![Image](https://miro.medium.com/1%2AL28uM0LnX5P2PglUDpI-ig.png)

Site: [https://certspotter.com](https://certspotter.com/)

Também consulta logs de Certificate Transparency.

Possui API e integração automatizada.

---

# 3. WAF Bypass via OSINT

Situação comum:

1. Servidor originalmente exposto direto.
    
2. Empresa contrata WAF.
    
3. DNS passa a apontar para o WAF.
    
4. IP real continua exposto.
    

Fontes para descobrir IP real:

- Histórico DNS
    
- Registros PTR
    
- Shodan
    
- Censys
    
- Certificados antigos
    
- Subdomínios que não passam pelo WAF
    

Se o IP real responder diretamente:

```
curl http://IP_REAL -H "Host: empresa.com"
```

Isso indica falha de configuração de firewall.

Importante: isso é identificação de exposição indevida, não exploração ativa.

---

# 4. Brute Force de Subdomínios

Quando o subdomínio não aparece em fontes públicas, utiliza-se brute force.

Exemplo de nomes testados:

```
dev
test
staging
api
admin
vpn
mail
internal
beta
homolog
portal
```

Ferramentas testam milhares de combinações automaticamente.

---

# SecLists

Repositório:  
[https://github.com/danielmiessler/SecLists](https://github.com/danielmiessler/SecLists)

Contém:

- Wordlists para brute force
    
- Listas de subdomínios comuns
    
- Listas baseadas em Alexa top domains
    

Exemplo de lista:

```
Discovery/DNS/subdomains-top1million-5000.txt
```

Uso com ferramenta:

```
ffuf -u https://FUZZ.empresa.com -w subdomains.txt
```

---

# 5. Ferramentas Ativas em Linux

## Sublist3r

![Image](https://miro.medium.com/1%2AuLYXTHjhC1740eCkelZWmw.png)

![Image](https://raw.githubusercontent.com/michele-tn/michele-tn/559bd571db12569c40f7ea4241cb5422c48f1cdd/1709576208241.jpg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2ATr3Rgz0ks6Ut91ENsO43Wg.png)

![Image](https://miro.medium.com/1%2AJw5wpJN8elpDXANMWTArwQ.png)

Ferramenta OSINT para enumeração passiva automatizada.

Instalação:

```
git clone https://github.com/aboul3la/Sublist3r.git
cd Sublist3r
pip3 install -r requirements.txt
```

Uso:

```
python3 sublist3r.py -d empresa.com
```

---

## Subfinder (ProjectDiscovery)

![Image](https://miro.medium.com/0%2AH1cyCuqZ6xUbjTeV)

![Image](https://opengraph.githubassets.com/10f9ca7c14e8c3833081be3e3ffb35dbf78c482453911f37eb9c6ae337b59c57/projectdiscovery/subfinder)

![Image](https://1.bp.blogspot.com/-2puOKv-Z7Yg/YUikd2uhUII/AAAAAAAAKWw/P7b3TZbVEwsuak6pbp5KgTX16ini3JCxwCLcBGAsYHQ/s16000/4.png)

![Image](https://www.kali.org/tools/subfinder/images/subfinder-logo.svg)

Ferramenta moderna e muito rápida.

Instalação (Linux com Go instalado):

```
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
```

Uso:

```
subfinder -d empresa.com
```

Modo ativo:

```
subfinder -d empresa.com -active
```

---

# 6. Pipeline Profissional com ProjectDiscovery

Ferramentas:

- subfinder
    
- dnsx
    
- httpx
    
- naabu
    

Instalação:

```
go install -v github.com/projectdiscovery/dnsx/cmd/dnsx@latest
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
```

Pipeline:

```
subfinder -d empresa.com > subs.txt
dnsx -l subs.txt > resolvidos.txt
httpx -l resolvidos.txt > ativos.txt
```

Fluxo:

1. Descobre subdomínios
    
2. Resolve DNS
    
3. Verifica quais estão ativos
    
4. Identifica serviços web expostos
    

---

# 7. Estratégia Completa de Enumeração

Fase 1 – Passiva:

- crt.sh
    
- CertSpotter
    
- SecurityTrails
    
- DNSDumpster
    
- Wayback
    
- Subfinder
    

Fase 2 – Consolidação:

- Remover duplicados
    
- Resolver DNS
    
- Identificar IPs
    
- Detectar WAF
    

Fase 3 – Ativa:

- Brute force DNS
    
- Verificação HTTP
    
- Identificação de IP real
    
