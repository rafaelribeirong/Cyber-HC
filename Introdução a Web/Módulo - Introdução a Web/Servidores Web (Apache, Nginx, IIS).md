# Documento único — Infra Web para Pentest (HTTP, servidores web, load balancer, configs) com imagens

## Imagens do documento (clique para abrir)

- Gráfico Netcraft (tendência): [grafico_netcraft_nginx_apache.png](sandbox:/mnt/data/grafico_netcraft_nginx_apache.png)
    
- Gráfico W3Techs (atual): [grafico_w3techs_atual.png](sandbox:/mnt/data/grafico_w3techs_atual.png)
    
- Diagrama Nginx (fluxo): [diagrama_nginx_fluxo.png](sandbox:/mnt/data/diagrama_nginx_fluxo.png)
    
- Diagrama Apache (fluxo): [diagrama_apache_fluxo.png](sandbox:/mnt/data/diagrama_apache_fluxo.png)
    
- Infográfico status codes: [infografico_status_codes_v2.png](sandbox:/mnt/data/infografico_status_codes_v2.png)
    
- Load balancer (3 diagramas):
    
    - [lb_diagrama_1.png](sandbox:/mnt/data/lb_diagrama_1.png)
        
    - [lb_diagrama_2_sticky.png](sandbox:/mnt/data/lb_diagrama_2_sticky.png)
        
    - [lb_diagrama_3_upload.png](sandbox:/mnt/data/lb_diagrama_3_upload.png)
        

---

## 1) O que é servidor web e como ele “serve a web”

Um **servidor web** é o software que recebe requisições **HTTP/HTTPS** (por exemplo `GET /login`) e devolve respostas (`200`, `404`, `502`, etc.) junto com **headers** e **conteúdo** (HTML, JSON, arquivo).

Ele pode:

- Servir **conteúdo estático** (HTML, CSS, JS, imagens, PDFs).
    
- Atuar como **reverse proxy** (encaminhar a requisição para um servidor da aplicação).
    
- Encaminhar PHP para **PHP-FPM** via **FastCGI**.
    
- Encerrar TLS (HTTPS), aplicar regras de roteamento, limitar requisições, comprimir, cachear e registrar logs.
    

**Ponto importante:** na maioria das arquiteturas modernas, o servidor web não “interpreta” a linguagem do seu sistema (Node/Python/Java). Ele encaminha para o processo da aplicação (app server). Com PHP, é comum o servidor web encaminhar para o **PHP-FPM**.

---

## 2) Os 2 mais usados hoje: Nginx e Apache (contexto de mercado)

### Uso atual (referência de mercado)

O W3Techs apresenta percentuais de uso atuais de servidores web e normalmente mostra **nginx** e **Apache** como os líderes.  
Veja o gráfico atual:  
[grafico_w3techs_atual.png](sandbox:/mnt/data/grafico_w3techs_atual.png)

### Evolução ao longo do tempo (tendência)

O Netcraft tem surveys ao longo dos anos, e dá para observar mudanças de participação (valores variam conforme metodologia).  
Veja o gráfico de tendência:  
[grafico_netcraft_nginx_apache.png](sandbox:/mnt/data/grafico_netcraft_nginx_apache.png)

**Resumo prático (para pentest):**

- **Nginx** aparece muito como **reverse proxy**, **TLS termination**, **cache** e até **load balancer**.
    
- **Apache** aparece muito em ambientes legados e também modernos (módulos, flexibilidade, `.htaccess` em alguns cenários).
    

---

## 3) Como uma requisição passa pela infraestrutura (visão visual)

### Fluxo típico com Nginx

Diagrama: [diagrama_nginx_fluxo.png](sandbox:/mnt/data/diagrama_nginx_fluxo.png)

O que esse fluxo mostra:

- Cliente → Nginx
    
- Nginx pode servir **estático**
    
- ou pode encaminhar para **App Server**
    
- ou pode encaminhar para **PHP-FPM**
    
- e devolve a resposta HTTP para o cliente
    

### Fluxo típico com Apache

Diagrama: [diagrama_apache_fluxo.png](sandbox:/mnt/data/diagrama_apache_fluxo.png)

O que esse fluxo mostra:

- Cliente → Apache
    
- Apache usa módulos (SSL, rewrite, proxy, etc.)
    
- Serve estático do `DocumentRoot`
    
- Pode atuar como proxy para app server
    
- Pode integrar PHP (por PHP-FPM ou mod_php dependendo do ambiente)
    

---

## 4) Status code: o que é e como interpretar em pentest

**Status code** é um número na resposta HTTP que diz o resultado da requisição.

Infográfico: [infografico_status_codes_v2.png](sandbox:/mnt/data/infografico_status_codes_v2.png)

Classes (o essencial):

- **2xx**: sucesso (ex: 200 OK, 201 Created)
    
- **3xx**: redirecionamento (ex: 301, 302; normalmente com `Location`)
    
- **4xx**: erro do lado do cliente (ex: 401, 403, 404)
    
- **5xx**: erro do lado do servidor/proxy/upstream (ex: 500, 502, 503)
    

**Como isso ajuda em pentest (interpretação):**

- **302 para /login** pode indicar que aquele endpoint existe, mas exige sessão/autenticação.
    
- **403** pode indicar recurso existente, mas bloqueado por permissão/WAF/regra.
    
- **502/504** pode indicar problemas na comunicação com o backend (app server) ou timeout.
    

---

## 5) Load balancer: conceito e por que você vai encontrar em site grande

### Conceito

Um **load balancer** fica na frente de múltiplos servidores e distribui as requisições entre eles. Ele também costuma fazer **health checks** para não enviar tráfego para servidores indisponíveis.

### Por que site grande usa

- Um servidor único pode saturar ou cair, derrubando o site.
    
- Com load balancer + múltiplos servidores, o site aguenta picos e falhas.
    

### Diagrama — servidor único vs load balancer

[lb_diagrama_1.png](sandbox:/mnt/data/lb_diagrama_1.png)

---

## 6) Stickiness (session affinity): por que importa

### Sem stickiness

O usuário pode cair em servidores diferentes a cada requisição.  
Se a aplicação guarda sessão localmente, isso pode causar inconsistência (logout, carrinho sumindo, etc.).

### Com stickiness

O load balancer tenta manter o mesmo usuário no mesmo servidor para preservar sessão local.

Diagrama:  
[lb_diagrama_2_sticky.png](sandbox:/mnt/data/lb_diagrama_2_sticky.png)

**Impacto no pentest:**

- Um teste pode “parecer instável” porque você caiu em nós diferentes.
    
- Para evidência, você precisa registrar requisições e observar padrão (status, redirects, cookies).
    

---

## 7) Upload em ambiente com load balancer (ponto crítico que você citou)

Diagrama:  
[lb_diagrama_3_upload.png](sandbox:/mnt/data/lb_diagrama_3_upload.png)

### Problema clássico

- Upload vai para o **Servidor A**
    
- Arquivo fica no **storage local do A**
    
- Na hora de acessar, você cai no **Servidor B**
    
- O arquivo não existe no B
    

### Solução típica em produção

- O arquivo vai para **storage compartilhado** (ex: object storage / NFS / serviço central)
    
- Qualquer servidor pode ler o mesmo arquivo
    

**Por que isso importa em pentest:**

- Se você está validando persistência, comportamento pode variar por nó.
    
- Você precisa testar consistência e registrar quando ocorre (sem assumir que é “bug aleatório”).
    

---

## 8) Como servidores web “interpretam” linguagens hoje

### Regra geral (moderno)

- Nginx/Apache: recebem HTTP, fazem roteamento e entregam resposta.
    
- App server (Node/Python/Java): executa lógica de negócio.
    
- Banco/serviços: armazenam e processam dados.
    

### Casos comuns

- **Node.js**: Nginx/Apache fazem proxy para o processo Node (ex: porta 3000).
    
- **Python**: Nginx/Apache fazem proxy para Gunicorn/uWSGI (varia).
    
- **Java**: Nginx/Apache fazem proxy para Tomcat/Spring Boot.
    
- **PHP**: Nginx/Apache encaminham para **PHP-FPM** (FastCGI) ou Apache pode usar mod_php (menos recomendado em muitos cenários modernos).
    

---

## 9) Configurações e arquivos: Nginx (com exemplos completos)

### Estrutura típica

- Arquivo principal: `nginx.conf`
    
- Inclui arquivos por site (varia por distro)
    

### Conceitos de configuração

- `http {}`: contexto HTTP global
    
- `server {}`: um virtual host (um site)
    
- `location {}`: regra por caminho/regex
    
- `upstream {}`: grupo de servidores de aplicação (balanceamento/failover)
    

### Exemplo Nginx: estático + proxy + PHP-FPM (comentado)

```nginx
http {
  # Grupo de backends (app server)
  upstream app_backend {
    server 127.0.0.1:3000;
  }

  server {
    listen 80;
    server_name exemplo.com;

    # Estático
    root /var/www/exemplo/public;
    index index.html index.htm;

    # Se existir arquivo, serve; se não, manda para @app
    location / {
      try_files $uri $uri/ @app;
    }

    # Reverse proxy para app (Node/Python/Java)
    location @app {
      proxy_pass http://app_backend;
      proxy_set_header Host $host;
      proxy_set_header X-Real-IP $remote_addr;
    }

    # PHP via PHP-FPM
    location ~ \.php$ {
      include fastcgi_params;
      fastcgi_pass unix:/run/php/php-fpm.sock;  # ou 127.0.0.1:9000
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
    }
  }
}
```

**O que esse config “faz” na prática:**

- Decide estático vs dinâmico.
    
- Encaminha dinâmico para backend.
    
- Encaminha PHP para o FPM.
    
- Monta headers que ajudam o backend a saber host e IP original.
    

---

## 10) Configurações e arquivos: Apache (com exemplos completos)

### Conceitos de configuração

- Config base (`httpd.conf` e/ou arquivos incluídos)
    
- `<VirtualHost>`: define um site
    
- `DocumentRoot`: pasta de estáticos
    
- Módulos: SSL, rewrite, proxy, etc.
    
- `.htaccess` (quando habilitado): regras por diretório
    

### Exemplo Apache: VirtualHost + estático + reverse proxy (comentado)

```apache
<VirtualHost *:80>
  ServerName exemplo.com
  DocumentRoot "/var/www/exemplo/public"

  ErrorLog  "/var/log/apache2/exemplo_error.log"
  CustomLog "/var/log/apache2/exemplo_access.log" combined

  <Directory "/var/www/exemplo/public">
    Options -Indexes
    AllowOverride None
    Require all granted
  </Directory>

  # Reverse proxy para app server
  ProxyPreserveHost On
  ProxyPass        "/"  "http://127.0.0.1:3000/"
  ProxyPassReverse "/"  "http://127.0.0.1:3000/"
</VirtualHost>
```

**O que esse config faz:**

- Serve estático do `DocumentRoot`
    
- Encaminha tudo para o backend (dependendo do objetivo, você pode combinar regras)
    
- Mantém o Host (útil para apps que dependem do host original)
    

---

## 11) O que você observa disso em pentest (sem “receitas”)

### Quando tem reverse proxy / load balancer

Você precisa olhar:

- Padrões de status code (principalmente 301/302/403/404/5xx)
    
- Cookies e possíveis cookies de afinidade
    
- Respostas inconsistentes (pode ser rotação de nó)
    
- Possível separação de estático e dinâmico (CDN + LB + app)
    

### Quando tem upload

Você precisa validar:

- Consistência do acesso ao arquivo
    
- Se existe storage compartilhado (comportamento consistente)
    
- Se há stickiness impactando o fluxo
    
