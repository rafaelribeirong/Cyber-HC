## 1) Um servidor único vs site com Load Balancer

![Image](https://www.researchgate.net/publication/314298900/figure/fig1/AS%3A469646819237890%401488983935508/Single-Server-versus-Multiple-Servers-with-a-load-balancer.png)

![Image](https://www.wisdomgeek.com/wp-content/uploads/2021/01/load-balancing-multiple-tiers-1024x472.png)

![Image](https://developers.cloudflare.com/_astro/lb-ref-arch-28-ALT.Dwf-s8s__1NmnXS.svg)

### Explicação

**Sem load balancer**

- Todo mundo acessa **um único servidor**
    
- Se ele cair, o site cai
    
- Se tiver muito acesso, ele satura
    

**Com load balancer (cenário comum em AWS, Azure, GCP)**

- O usuário acessa **um ponto único**
    
- O load balancer distribui as requisições
    
- Existem vários servidores “iguais” por trás
    
- Se um cair, os outros continuam
    

👉 Em sites grandes, **é praticamente obrigatório** usar load balancer.  
Um site grande hospedado só em um servidor **não aguentaria tráfego real**.

---

## 2) Load Balancer com e sem stickiness (session affinity)

![Image](https://www.imperva.com/learn/wp-content/uploads/sites/13/2019/01/session-stickiness-diagram.jpg)

![Image](https://docs.cloud.google.com/static/run/docs/images/session-affinity-diagram.svg)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240704160512/With-and-Without-Sticky-Sessions.webp)

### Sem stickiness

- Requisição 1 → Servidor A
    
- Requisição 2 → Servidor B
    
- Requisição 3 → Servidor C
    

Se a sessão estiver salva **localmente no servidor**, isso pode causar:

- logout inesperado
    
- erro de permissão
    
- comportamento inconsistente
    

### Com stickiness (afinidade de sessão)

- O load balancer “lembra” o usuário
    
- Todas as requisições vão para o **mesmo servidor**
    
- Muito comum quando a aplicação não usa sessão compartilhada
    

 **Como pentester**, isso importa porque:

- Um teste pode funcionar em uma requisição e falhar na outra
    
- Um bypass pode parecer “instável”, mas é o balanceamento causando isso
    

---

## 3) Upload de arquivos em ambiente com Load Balancer (ponto CRÍTICO)

![Image](https://media.geeksforgeeks.org/wp-content/uploads/20240213114444/lb2.webp)

![Image](https://s26500.pcdn.co/wp-content/uploads/2019/07/storage-load-balancing-diagram.svg)

![Image](https://miro.medium.com/v2/resize%3Afit%3A2000/1%2Aky2kuFOIj8xeS4T5gW2ZpA.png)

### Problema clássico

1. Você faz upload
    
2. A requisição cai no **Servidor A**
    
3. O arquivo é salvo **localmente**
    
4. Depois você tenta acessar o arquivo
    
5. A requisição cai no **Servidor B**
    
6. O arquivo “não existe”
    

Isso acontece **o tempo todo** quando:

- há load balancer
    
- não há storage compartilhado
    
- não há stickiness
    

### Solução usada em produção

- Upload vai para **storage compartilhado**
    
    - Exemplo: bucket, NFS, serviço de arquivos, CDN
        
- Todos os servidores acessam o mesmo local
    

---

## Por que isso é MUITO importante no pentest web

Você falou algo **extremamente correto**:

> “se faço upload no site ele pode ir pra um servidor mas não para outro”

Isso impacta diretamente:

### 1) Exploração de upload

- Um arquivo pode “funcionar às vezes”
    
- Exploit pode parecer quebrado
    
- Na verdade, você está caindo em servidores diferentes
    

### 2) Evidência de falha

- Você precisa testar **várias vezes**
    
- Observar padrões (status code, resposta, redirect)
    
- Não assumir que falhou na primeira tentativa
    

### 3) Identificação indireta de Load Balancer

Durante exploração autorizada, sinais comuns:

- comportamento inconsistente
    
- cookies extras (stickiness)
    
- headers de proxy
    
- respostas levemente diferentes
    
- tempo de resposta variando
    

---

## Resumo mental para pentest (guarda isso)

- Site grande → **assuma que tem load balancer**
    
- Load balancer → múltiplos servidores
    
- Múltiplos servidores → comportamento pode variar
    
- Upload + storage local → falha intermitente
    
- Sessão local sem stickiness → bugs estranhos
    
- Sempre observe **padrões**, não uma única resposta
    
