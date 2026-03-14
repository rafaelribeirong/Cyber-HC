# Web Application Firewall (WAF)

## 1) O que é um Web Application Firewall

Um **Web Application Firewall (WAF)** é uma **camada de segurança** projetada para **inspecionar, filtrar e bloquear tráfego HTTP/HTTPS malicioso** antes que ele chegue à aplicação web.

Diferente de um firewall tradicional (rede), o WAF **entende a linguagem da web**:

- URLs
    
- parâmetros
    
- headers
    
- cookies
    
- payloads (GET, POST, JSON, form-data)
    

Ele atua **no nível da aplicação**.

---

## 2) Para que serve um WAF (objetivo real)

O WAF existe para:

- Reduzir risco de ataques web comuns
    
- Proteger aplicações que **não podem ser alteradas rapidamente**
    
- Criar uma **camada extra de defesa** entre a internet e a aplicação
    

Principais ataques mitigados:

- SQL Injection
    
- XSS
    
- CSRF (parcialmente)
    
- Path Traversal
    
- File Inclusion
    
- Upload malicioso
    
- Flood de requisições (rate limit)
    

---

## 3) Analogia simples (casa / empresa)

### Exemplo: sua casa

```
Rua (internet)
  ↓
Portão (Firewall de rede)
  ↓
Porteiro (WAF)
  ↓
Cômodos da casa (Aplicação)
```

- **Firewall de rede**: só deixa entrar quem usa a porta certa (80/443)
    
- **WAF**: olha quem você é, o que você está pedindo e **como** está pedindo
    
- **Aplicação**: onde os dados realmente estão
    

O WAF é o **porteiro que entende o idioma da web**.

---

## 4) Onde o WAF fica na arquitetura

### Arquitetura moderna comum

![Image](https://www.indusface.com/wp-content/uploads/2021/12/Internal-How-does-a-WAF-Work-1.png)

![Image](https://learn.microsoft.com/en-us/azure/web-application-firewall/media/cdn-overview/waf-cdn-overview.png)

![Image](https://www.indusface.com/wp-content/uploads/2023/04/Forward-proxy-vs-reverse-proxy-1.png)

Fluxo típico:

```
Usuário
  ↓
CDN (opcional)
  ↓
WAF
  ↓
Load Balancer
  ↓
Aplicação
```

O WAF pode estar:

- integrado à CDN
    
- como reverse proxy
    
- como appliance dedicado
    
- como módulo do servidor web
    

---

## 5) WAF ≠ Firewall tradicional

### Firewall tradicional (rede)

- Filtra IP, porta, protocolo
    
- Não entende HTTP em profundidade
    

### WAF

- Entende requisições web
    
- Analisa:
    
    - `/login?user=admin'--`
        
    - `<script>alert(1)</script>`
        
    - headers estranhos
        
    - padrões de ataque conhecidos
        

Resumo:

> Firewall protege a **rede**  
> WAF protege a **aplicação**

---

## 6) O que o WAF analisa na requisição HTTP

O WAF observa praticamente tudo:

- Método HTTP (GET, POST, PUT…)
    
- URL e rota
    
- Query string
    
- Body (JSON, form-data, XML)
    
- Cookies
    
- Headers
    
- Frequência de requisições
    
- Comportamento do cliente
    

Exemplo:

```
POST /login
user=admin' OR '1'='1
```

O WAF pode identificar isso como padrão de SQL Injection e bloquear.

---

## 7) Rotas de aplicação (por que isso importa)

### O que é uma rota de aplicação

Uma **rota** é o caminho que a aplicação expõe:

- `/login`
    
- `/api/users`
    
- `/admin/dashboard`
    
- `/upload`
    

O WAF pode ter regras específicas por rota.

### Exemplo prático (empresa)

```
/login           → regra mais restrita
/api/public      → regra mais permissiva
/admin           → bloqueio por IP + autenticação
/upload          → inspeção pesada de conteúdo
```

Isso é **muito comum em ambientes corporativos**.

---

## 8) Exemplo prático: empresa pequena

```
Internet
  ↓
WAF
  ↓
Servidor Web
  ↓
Sistema interno (ERP)
```

O WAF:

- bloqueia tentativas de SQLi
    
- limita requisições por IP
    
- registra logs de ataque
    
- protege mesmo se o código tiver falhas
    

---

## 9) Exemplo prático: site grande

```
Usuário
  ↓
CDN + WAF (Cloudflare, etc.)
  ↓
Load Balancer
  ↓
Vários servidores de aplicação
```

Aqui o WAF:

- absorve ataques
    
- bloqueia payloads conhecidos
    
- pode desafiar o usuário (captcha)
    
- esconde o IP real do servidor
    

---

## 10) Tipos de WAF (como você vai encontrar)

### WAF baseado em assinatura

- Bloqueia padrões conhecidos
    
- Rápido de implementar
    
- Pode gerar falso positivo
    

### WAF baseado em comportamento

- Analisa padrões de uso
    
- Mais inteligente
    
- Mais complexo
    

### WAF híbrido

- Combina ambos
    
- Mais comum hoje
    

---

## 11) WAF na prática do pentest (raciocínio correto)

No pentest web, o WAF muda **como você interpreta respostas**, não apenas o resultado.

### Situações comuns:

- Payload bloqueado com 403
    
- Resposta alterada (HTML de erro)
    
- Rate limit (429)
    
- CAPTCHA inesperado
    
- Headers específicos do WAF
    

Isso **não significa automaticamente** que:

- a aplicação é segura
    
- a falha não existe
    

Significa:

> “Existe uma camada intermediária interferindo”

---

## 12) Exemplo clássico de confusão

Você testa:

```
<input value="<script>alert(1)</script>">
```

Resultado:

- WAF bloqueia → 403
    

Isso indica:

- o WAF funcionou
    
- **não prova** que o backend trata corretamente
    

Por isso, em relatório, você documenta:

- presença do WAF
    
- impacto na testagem
    
- camada que bloqueou
    

---

## 13) O que um WAF NÃO faz

Importante para não criar falsa sensação de segurança:

- Não corrige código vulnerável
    
- Não substitui validação no backend
    
- Não garante segurança total
    
- Não protege falhas lógicas
    

O WAF é **camada complementar**, não solução final.

---

## 14) Como identificar um WAF em um alvo

Sinais comuns:

- Headers específicos
    
- Respostas padrão de bloqueio
    
- Desafios (JS, captcha)
    
- Rate limit agressivo
    
- IPs pertencentes a provedores conhecidos
    

Exemplo de header:

```
Server: cloudflare
```

---

## 15) Resumo final (para suas anotações)

- WAF = firewall de aplicação web
    
- Entende HTTP/HTTPS
    
- Analisa payloads, rotas e comportamento
    
- Fica entre internet e aplicação
    
- Muito comum integrado a CDNs
    
- Impacta diretamente o pentest
    
- Deve ser documentado no relatório
    

---

## Conclusão importante (mentalidade correta)

> **Como pentester, você não “briga” com o WAF.  
> Você entende que ele existe, documenta e ajusta sua análise.**
