## Domain Name System (DNS)

### Conceitos básicos

- **DNS (Domain Name System)**  
    Sistema responsável por traduzir nomes de domínio em endereços IP.
    
- **CGI.br**  
    Comitê Gestor da Internet no Brasil.
    
- **Registro.br**  
    Entidade responsável pelo registro e administração de domínios **.br**.
    
- **TLD (Top-Level Domain)**  
    Domínio de topo, como:
    
    - `.com`
        
    - `.org`
        
    - `.net`
        
    - `.br`
        
    - `.com.br`
        

---

## Estrutura de um domínio

Exemplo:

```
www.seuendereco.com.br
```

- `www` → subdomínio
    
- `seuendereco` → domínio
    
- `com.br` → TLD (domínio de topo)
    

---

## Como funciona a resolução DNS

Antes de qualquer acesso, o **servidor DNS local** precisa saber **quem é o responsável pelo TLD** solicitado.

Fluxo completo de resolução DNS:

```
Notebook
  ↓
Servidor DNS local
  ↓
Root Server
  ↓
Servidor DNS do TLD (.br)
  ↓
Servidor DNS autoritativo (seuendereco.com.br)
  ↓
Servidor DNS local
  ↓
Notebook
```

Explicação resumida:

1. O notebook consulta o **DNS local**.
    
2. O DNS local pergunta ao **Root Server** quem responde pelo TLD.
    
3. O Root Server indica o **servidor do TLD** (ex: .br).
    
4. O DNS local consulta o **servidor do TLD**.
    
5. O TLD informa qual é o **DNS autoritativo do domínio**.
    
6. O DNS autoritativo retorna o IP correto.
    
7. O DNS local entrega a resposta ao notebook.
    

![Image](https://www.researchgate.net/publication/342003872/figure/fig2/AS%3A900085244248066%401591608453435/Domain-name-resolution-process-with-DNS.ppm)



![Image](https://www.indusface.com/wp-content/uploads/2024/10/DNS-lookup-process-.png)

---

## Root Servers (Servidores Raiz)

Existem **13 Root Servers**, identificados por letras:

```
a.root-servers.net
b.root-servers.net
c.root-servers.net
d.root-servers.net
e.root-servers.net
f.root-servers.net
g.root-servers.net
h.root-servers.net
i.root-servers.net
j.root-servers.net
k.root-servers.net
l.root-servers.net
m.root-servers.net
```

Observação importante:  
Cada letra representa **vários servidores físicos espalhados pelo mundo**, usando Anycast.

---

## Ferramenta `dig`

Ferramenta utilizada para consultas DNS detalhadas.

### Instalação do `dig`

**Debian / Ubuntu**

```
sudo apt update
sudo apt install dnsutils -y
```

**CentOS / Rocky / AlmaLinux**

```
sudo yum install bind-utils -y
```

ou (em versões mais novas):

```
sudo dnf install bind-utils -y
```

**Arch Linux**

```
sudo pacman -S bind
```

**macOS (Homebrew)**

```
brew install bind
```

### Exemplo de uso

```
dig seuendereco.com.br
```
