## Tabela de registros DNS

Domínio base: `seudominio.com.br`

|Subdomínio|Tipo|Valor|
|---|---|---|
|lab|A|192.168.1.10|
|@|A|192.168.1.11|
|seudominio.com.br|A|192.168.1.11|
|lab.seudominio.com.br|A|192.168.1.10|
|swh.seudominio.com.br|A|1.2.3.4|

Observações:

- `@` representa o **domínio raiz** (`seudominio.com.br`)
    
- O subdomínio `lab` aponta para um IP diferente do domínio principal
    

---

## Tipos de registros DNS e para que servem

### A – Address Record (IPv4)

Serve para apontar um nome para um endereço IPv4.

Exemplo:

```
lab.seudominio.com.br → 192.168.1.10
```

Uso prático:

- Hospedagem de sites
    
- Servidores internos
    
- Aplicações web
    

---

### AAAA – Address Record (IPv6)

Mesma função do registro A, porém usando IPv6.

Exemplo:

```
app.seudominio.com.br → 2001:db8::1
```

Uso prático:

- Infraestrutura moderna
    
- Ambientes que exigem IPv6
    

---

### CNAME – Canonical Name

Cria um **apelido** apontando para outro domínio, e não diretamente para um IP.

Exemplo:

```
www.seudominio.com.br → CNAME → swh.seudominio.com.br
swh.seudominio.com.br → A → 1.2.3.4
```

Funcionamento:

- O cliente resolve o CNAME
    
- Depois resolve o A do destino final
    

Uso prático:

- Integração com serviços externos
    
- CDN
    
- Serviços em nuvem
    

#### Atenção – Subdomain Takeover (breve)

Se um CNAME aponta para um serviço externo que **não existe mais**, o subdomínio pode ser assumido por terceiros.

Exemplo de risco:

```
swh.seudominio.com.br → CNAME → servico-cloud-inativo.com
```

Se alguém registrar esse serviço externo novamente, pode assumir o subdomínio.

---

### TXT – Text Record

Armazena **informações em texto**, muito usado para validações.

Exemplos comuns:

- Validação de domínio
    
- SPF
    
- DKIM
    
- DMARC
    

Exemplo simples:

```
seudominio.com.br → TXT → "verificacao=google123"
```

Uso prático:

- Provar que você é dono do domínio
    
- Configurar segurança de e-mail
    

---

### MX – Mail Exchange

Define **quais servidores recebem e-mails** do domínio.

Exemplo:

```
seudominio.com.br → MX → mail.seudominio.com.br (prioridade 10)
```

Fluxo simples:

- Alguém envia e-mail para @seudominio.com.br
    
- O servidor consulta o MX
    
- Entrega no servidor definido
    

Uso prático:

- Funcionamento de e-mails corporativos
    

---

### SOA – Start of Authority

Registro principal da zona DNS. Define **autoridade e parâmetros de controle**.

Exemplo (simplificado):

```
seudominio.com.br → SOA → ns1.seudominio.com.br admin.seudominio.com.br
```

Contém:

- Servidor DNS primário
    
- E-mail do administrador
    
- Controle de cache e atualizações
    

Uso prático:

- Sincronização entre servidores DNS
    
- Validação da zona DNS
    

---

### NS – Name Server

Define **quais servidores são autoritativos** pelo domínio.

Exemplo:

```
seudominio.com.br → NS → ns1.seudominio.com.br
seudominio.com.br → NS → ns2.seudominio.com.br
```

Uso prático:

- Indicar onde o DNS oficial do domínio está hospedado
    
- Essencial para funcionamento do domínio
    

---

## Resumo rápido

- A / AAAA → apontam para IP
    
- CNAME → apelido para outro domínio
    
- TXT → validações e segurança
    
- MX → servidores de e-mail
    
- SOA → controle e autoridade da zona
    
- NS → servidores DNS autoritativos
    
