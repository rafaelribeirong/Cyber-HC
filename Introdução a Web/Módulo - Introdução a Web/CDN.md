# CDN – Content Delivery Network

## 1) O que é CDN

**CDN (Content Delivery Network)** é uma **rede distribuída de servidores** espalhados geograficamente que tem como objetivo **entregar conteúdo web mais rápido, mais disponível e mais seguro** para o usuário final.

Em vez de todo mundo acessar **um único servidor central**, o conteúdo é entregue a partir de um **servidor mais próximo do usuário**.

---

## 2) Empresas que oferecem CDN

CDN não é uma tecnologia isolada, é um **serviço** oferecido por várias empresas.

Alguns exemplos comuns que você vai encontrar em ambientes reais:

- Cloudflare
    
- Amazon CloudFront
    
- Akamai
    
- Fastly
    
- Google Cloud CDN
    
- Azure CDN
    

No pentest web, **Cloudflare e CloudFront** são extremamente comuns.

---

## 3) Como a web funciona SEM CDN (modelo tradicional)

### Fluxo sem CDN

```
Usuário (Brasil)
        |
        | HTTP/HTTPS
        v
Servidor único (EUA)
```

### Problemas desse modelo

- Alta latência (demora para carregar)
    
- Servidor sobrecarregado
    
- Se o servidor cair → site fora do ar
    
- Ataques (DDoS) atingem direto o servidor
    

---

## 4) Como funciona uma CDN (conceito visual)

### Fluxo COM CDN

![Image](https://substackcdn.com/image/fetch/%24s_%21rycF%21%2Cf_auto%2Cq_auto%3Agood%2Cfl_progressive%3Asteep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fd2785489-6c63-40cf-bb4a-1b8656a81d01_1600x1104.png)

![Image](https://www.cloudflare.com/img/learning/cdn/glossary/edge-server/cdn-edge-network-device.png)

![Image](https://scaleyourapp.com/wp-content/uploads/2020/07/CDN-and-load-balancer-grid.jpeg)

```
Usuário (Brasil)
        |
        v
Servidor CDN (Brasil)  ← cache
        |
        v
Servidor de origem (Origin Server)
```

### Passo a passo real

1. Usuário acessa `https://site.com`
    
2. O DNS aponta para a **CDN**, não direto para o servidor real
    
3. A CDN verifica:
    
    - Já tenho esse conteúdo em cache?
        
        - Sim → entrega direto
            
        - Não → busca no **servidor de origem**
            
4. A CDN:
    
    - entrega ao usuário
        
    - guarda em cache para próximos acessos
        

---

## 5) O que a CDN entrega (na prática)

### Conteúdo mais comum em CDN

- Imagens (`.jpg`, `.png`, `.webp`)
    
- CSS (`.css`)
    
- JavaScript (`.js`)
    
- Fontes (`.woff`, `.ttf`)
    
- Vídeos
    
- Arquivos estáticos em geral
    

### Em muitos sites modernos

- **Quase tudo passa pela CDN**
    
- Inclusive HTML e respostas de API (dependendo da configuração)
    

---

## 6) CDN + Cache (ponto-chave)

A CDN trabalha fortemente com **cache**.

### Exemplo prático

```
Primeiro acesso:
Usuário → CDN → Servidor de origem → CDN → Usuário

Segundo acesso:
Usuário → CDN (cache HIT) → Usuário
```

Headers importantes que você vai ver:

- `Cache-Control`
    
- `Expires`
    
- `Age`
    
- `CF-Cache-Status` (Cloudflare)
    
- `X-Cache` (ou similares)
    

No pentest, esses headers **denunciam CDN**.

---

## 7) CDN NÃO é só performance (é também segurança)

CDNs modernas fazem muito mais que cache.

### Serviços comuns embutidos

- Proteção contra **DDoS**
    
- **WAF** (Web Application Firewall)
    
- Rate limiting
    
- TLS/HTTPS
    
- Ocultação do servidor de origem
    

Ou seja: **a CDN vira uma camada de defesa** na frente da aplicação.

---

## 8) CDN + Load Balancer (diferença importante)

Muita gente confunde.

### CDN

- Foco: **entrega de conteúdo**
    
- Cache distribuído
    
- Fica na **borda (edge)** da internet
    

### Load Balancer

- Foco: **distribuir requisições**
    
- Trabalha entre servidores de backend
    
- Fica **dentro da infraestrutura**
    

Arquitetura comum em sites grandes:

```
Usuário
  ↓
CDN
  ↓
Load Balancer
  ↓
Servidores de aplicação
```

---

## 9) Exemplos práticos (realidade de pentest)

### Exemplo 1 – HTML servido por CDN

Você acessa a home do site.

- A resposta vem rápido
    
- Headers indicam cache
    
- O servidor real **não é exposto**
    

Se você tentar resolver IP:

- Vai cair em IP da CDN
    
- Não no servidor real
    

---

### Exemplo 2 – Upload e CDN (atenção)

Uploads normalmente **não ficam em cache**.

Fluxo típico:

```
Upload → CDN → Servidor de origem
```

Mas:

- Download do arquivo pode passar pela CDN depois
    
- Dependendo do cache e headers
    

No pentest:

- Upload pode funcionar
    
- Mas acesso ao arquivo pode variar (cache, invalidação, múltiplos nós)
    

---

### Exemplo 3 – CDN + WAF

A CDN pode:

- Bloquear payloads suspeitos
    
- Alterar respostas (403, 429)
    
- Injetar páginas de challenge (CAPTCHA)
    

Isso **impacta diretamente testes**:

- Um payload pode falhar na CDN
    
- Mas não significa que o backend esteja seguro
    

---

## 10) Como identificar uma CDN em um alvo

Sinais comuns:

### Headers HTTP

- `Server: cloudflare`
    
- `CF-Ray`
    
- `CF-Cache-Status`
    
- `X-Cache`
    
- `Via`
    

### DNS

- IP resolve para ranges conhecidos de CDN
    
- ASN da CDN
    

### Comportamento

- Resposta extremamente rápida
    
- Mesma resposta de IPs diferentes
    
- Cache HIT/MISS
    

---

## 11) Impacto direto em pentest web (raciocínio correto)

Como pentester, CDN muda sua **interpretação**, não a técnica em si.

### Pontos críticos

- Você pode **não estar falando direto com o servidor**
    
- Erros podem vir do WAF da CDN
    
- Rate limit pode ser da CDN, não da aplicação
    
- IP real do servidor pode estar oculto
    
- Cache pode mascarar mudanças
    

### Conclusão prática

> “Se tem CDN, minha primeira camada de interação NÃO é a aplicação.”

Você testa:

- comportamento
    
- headers
    
- cache
    
- respostas inconsistentes  
    antes de tirar conclusões.
    

---

## 12) Resumo rápido (para suas anotações)

- CDN = rede de servidores distribuídos
    
- Entrega conteúdo mais rápido e mais seguro
    
- Faz cache na borda (edge)
    
- Pode incluir WAF, DDoS protection e rate limit
    
- Oculta o servidor de origem
    
- Impacta testes de:
    
    - upload
        
    - enumeração
        
    - rate limit
        
    - respostas HTTP
        
- Não substitui load balancer, trabalha junto
    
